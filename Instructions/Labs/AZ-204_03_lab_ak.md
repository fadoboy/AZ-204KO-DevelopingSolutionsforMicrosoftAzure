---
lab:
    title: '랩: .NET용 Azure Storage SDK를 사용하여 Azure Storage 리소스 및 메타데이터 검색'
    module: '모듈 03: BLOB 스토리지를 사용하는 솔루션 개발'
    type: 'Answer Key'
---

# 랩: .NET용 Azure Storage SDK를 사용하여 Azure Storage 리소스 및 메타데이터 검색
# 학생 랩 Answer Key

## Microsoft Azure 사용자 인터페이스

Microsoft 클라우드 도구의 동적 특성을 감안할 때, 이 교육 콘텐츠를 개발한 후 Azure UI가 변경될 수 있습니다. 이러한 변경으로 인해 랩 지침과 랩 단계가 일치하지 않을 수 있습니다.

Microsoft는 커뮤니티가 필요한 변경 사항을 제공하면 이 교육 과정을 업데이트합니다. 그러나 클라우드 업데이트가 자주 발생하기 때문에 이 교육 콘텐츠가 업데이트되기 전에 UI가 먼저 변경될 수 있습니다. **이 경우 변경 사항에 적응하고 필요에 따라 랩에서 작업합니다.**

## 지침

### 시작하기 전에

#### 랩 가상 머신에 로그인

다음 자격 증명을 사용하여 Windows 10 VM(가상 머신)에 로그인합니다.
    
-   사용자 이름: **관리자**

-   암호: **Pa55w.rd**

> **참고**: 강사가 가상 랩 환경 연결에 대한 지침을 제공합니다.

#### 설치된 응용 프로그램 리뷰

Windows 10 데스크톱에서 작업 표시줄을 찾습니다. 작업 표시줄에는 이 랩에서 사용할 애플리케이션에 대한 아이콘이 포함되어 있습니다.
    
-   Microsoft Edge

-   File Explorer

### 연습 1: Azure 리소스 만들기

#### 작업 1: Azure Portal 열기

1.  작업 표시줄에서 **Microsoft Edge** 아이콘을 선택합니다.

1.  열려 있는 브라우저 창에서 Azure Portal(<https://portal.azure.com>)로 이동합니다.

1.  Microsoft 계정의 이메일 주소를 입력한 다음 **다음** 을 선택합니다.

1.  Microsoft 계정의 암호를 입력한 다음 **로그인** 을 선택합니다.

    > **참고**: Azure Portal에 처음 로그인하는 경우 포털 둘러보기가 제공됩니다. 둘러보기를 건너뛰고 포털을 사용하려면 **시작하기** 를 선택합니다.

#### 작업 2: 스토리지 계정 만들기

1.  Azure Portal 탐색 창에서 **모든 서비스** 를 선택합니다.

1.  **모든 서비스** 블레이드에서 **스토리지 계정** 을 선택합니다.

1.  **스토리지 계정** 블레이드에서 스토리지 인스턴스 목록을 찾습니다.

1.  **스토리지 계정** 블레이드에서 **추가** 를 선택합니다.

1.  **기본** 탭 등 **스토리지 계정 만들기** 블레이드에서 탭을 찾습니다.

    > **참고**: 각 탭은 새 스토리지 계정을 만드는 워크플로의 단계를 나타냅니다. 언제든지 **검토 + 만들기** 를 선택하여 나머지 탭을 건너뛸 수 있습니다.

1.  **기본** 탭에서 다음 작업을 수행합니다.
    
    1.  **구독** 텍스트 박스를 기본값으로 설정된 상태로 둡니다.

    1.  **리소스 그룹** 섹션에서 **새로 만들기** 를 선택하고 **StorageMedia** 를 입력한 다음 **확인** 을 선택합니다.

    1.  **스토리지 계정 이름** 텍스트 상자에 **mediastor*[yourname]*** 을 입력합니다.

    1.  **위치** 드롭다운 목록에서 **(US) 미국 동부** 하위 지역을 선택합니다.

    1.  **성능** 섹션에서 **표준** 을 선택합니다.

    1.  **계정 종류** 드롭다운 목록에서 **StorageV2(범용 v2)** 를 선택합니다.

    1.  **복제** 드롭다운 목록에서 **RA-GRS(읽기 액세스 지역 중복 스토리지)** 를 선택합니다.

    1.  **액세스 계층** 섹션에서 **핫** 이  선택되어 있는지 확인합니다.

    1.  **검토 + 만들기** 를 선택합니다.

1.  **검토 + 만들기** 탭에서 이전 단계에서 선택한 옵션을 검토합니다.

1.  지정된 구성을 사용하여 스토리지 계정을 만들려면 **만들기** 를 선택합니다. 

    > **참고**: 이 랩을 진행하기 전에 만들기 작업이 완료될 때까지 기다립니다.

1.  Azure Portal 탐색 창에서 **모든 서비스** 를 선택합니다.

1.  **모든 서비스** 블레이드에서 **스토리지 계정** 을 선택합니다.

1.  **스토리지 계정** 블레이드에서 **mediastor*[yourname]*** 스토리지 계정 인스턴스를 선택합니다.

1.  **스토리지 계정** 블레이드에서 **설정** 섹션을 찾은 다음 **속성** 링크를 선택합니다.

1.  **속성** 섹션에서 **기본 엔드포인트 Blob service ** 텍스트 상자의 값을 기록합니다.

    > **참고**: 이 값은 랩에서 나중에 사용합니다.

1.  여전히 **스토리지 계정** 블레이드에서 **설정** 섹션을 찾은 다음 **액세스 키** 링크를 선택합니다.

1.  **액세스 키** 섹션에서 다음 작업을 수행합니다.

    1.  **스토리지 계정 이름** 텍스트 상자에 값을 기록합니다.
    
    1.  키 중 하나를 선택한 다음 **키** 상자 중 하나에 값을 기록합니다.

    > **참고**: 이 모든 값은 이 랩에서 나중에 사용합니다.

#### 검토

이 연습에서는 랩의 나머지 부분에서 사용할 새 스토리지 계정을 만들었습니다.

### 연습 2: 컨테이너에 BLOB 업로드

#### 작업 1: 스토리지 계정 컨테이너 만들기

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서, 이 랩의 앞에서 만든 **StorageMedia** 리소스 그룹을 찾아 선택합니다.

1.  **StorageMedia** 블레이드에서 이 랩의 앞에서 만든 **mediastor*[yourname]*** 스토리지 계정을 선택합니다.

1.  **스토리지 계정** 블레이드에서 **Blob 서비스** 섹션에 있는 **컨테이너** 링크를 선택합니다.

1.  **컨테이너** 섹션에서 **+ 컨테이너** 를 선택합니다.

1.  **새 컨테이너** 팝업 창에서 다음 작업을 수행합니다.
    
    1.  **이 름** 텍스트 상자에 **raster-graphics** 를 입력합니다.
    
    1.  **공용 액세스 수준** 드롭다운 목록에서 **프라이빗(익명 액세스 없음)** 를 선택하고 **확인** 을 선택합니다.

1.  **컨테이너** 섹션으로 돌아가서 **+ 컨테이너** 를 선택합니다.

1.  **새 컨테이너** 팝업 창에서 다음 작업을 수행합니다.
    
    1.  **이 름** 텍스트 박스에 **compressed-audio** 를 입력합니다.
    
    1.  **공용 액세스 수준** 드롭다운 목록에서 **프라이빗(익명 액세스 없음)** 를 선택하고 **확인** 을 선택합니다.

1.  **컨테이너** 섹션에서, 컨테이너의 업데이트된 목록을 관찰합니다.

#### 작업 2: 스토리지 계정 BLOB 업로드

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서, 이 랩의 앞에서 만든 **StorageMedia** 리소스 그룹을 찾아 선택합니다.

1.  **StorageMedia** 블레이드에서 이 랩의 앞에서 만든 **mediastor*[yourname]*** 스토리지 계정을 선택합니다.

1.  **스토리지 계정** 블레이드에서 **Blob 서비스** 섹션에 있는 **컨테이너** 링크를 선택합니다.

1.  **컨테이너** 섹션에서 최근에 만든 **raster-graphics** 컨테이너를 선택합니다.

1.	**컨테이너** 블레이드에서 **업로드** 를 선택합니다.

1.	**BLOB 업로드** 창에서 다음 작업을 수행합니다.

    1.  **파일** 섹션에서 **폴더** 아이콘을 선택합니다.

    1.  **파일 탐색기** 창에서 **Allfiles (F):\\Allfiles\\Labs\\03\\Starter\\Images** 로 이동하여 **graph.jpg** 파일을 선택하고 **열기** 를 선택합니다.

    1.  **파일이 이미 있는 경우 덮어쓰기** 확인란이 선택되어 있는지 확인하고, **업로드** 를 선택합니다. 
    
    > **참고**: 이 랩을 계속하기 전에 Blob이 업로드될 때까지 기다립니다.

#### 검토

이 연습에서는 스토리지 계정에 자리 표시자 컨테이너 몇 개를 만들고 컨테이너 중 하나를 BLOB으로 채웠습니다.

### 연습 3: .NET SDK를 사용하여 컨테이너에 액세스

#### 작업 1: .NET 프로젝트 만들기

1.  **시작** 화면에서 **Visual Studio Code** 타일을 선택합니다.

1.  **파일** 메뉴에서 **폴더 열기** 를 선택합니다.

1.  열리는 **파일 탐색기** 창에서 **Allfiles (F):\\Allfiles\\Labs\\03\\Starter\\BlobManager** 로 이동하여 **폴더 선택** 을 선택합니다.

1.  **Visual Studio Code** 창에서 탐색기 창의 바로 가기 메뉴를 마우스 오른쪽 단추로 클릭하거나 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 현재 폴더에서 **BlobManager** 라는 새 .NET 프로젝트를 만들기 위해 엔터를 선택합니다.

```
    dotnet new console --name BlobManager --output .
```

    > **참고**: **dotnet new** 명령은 새 **console** 프로젝트를 프로젝트와 이름이 같은 폴더에 만듭니다.

1.  명령 프롬프트에서 다음 명령을 입력하고 NuGet에서 **Azure.Storage.Blobs** 의 버전 12.0.0를 가져오기 위해  Enter 키를 선택합니다.

```
    dotnet add package Azure.Storage.Blobs --version 12.0.0
```

    > **참고**: **dotnet add package** 명령은 NuGet에서 **Azure.Storage.Blobs** 패키지를 추가합니다. 더 자세한 내용은 [Azure.Storage.Blobs](https://www.nuget.org/packages/Azure.Storage.Blobs/12.0.0)를 참조하세요.

1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 빌드합니다.

```
    dotnet build
```

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 2: 프로그램 클래스를 수정하여 스토리지에 액세스

1.  **Visual Studio Code** 창의 탐색기 창에서 **Program.cs** 파일을 엽니다.

1.  **Program.cs** 파일의 코드 편집기 탭에서 기존 파일의 모든 코드를 삭제합니다.

1.  다음 코드 줄을 추가하여 NuGet에서 가져온 **Azure.Storage.Blobs**  패키지에서 **Azure.Storage**, **Azure.Storage.Blobs**와 **Azure.Storage.Blobs.Models** 네임스페이스를 가져옵니다.

```
    using Azure.Storage;
    using Azure.Storage.Blobs;
    using Azure.Storage.Blobs.Models;
```
    
1.  다음 코드 줄을 추가하여 이 파일에 사용할 기본 제공 네임스페이스에 대해 **using** 지시문을 추가합니다.

```
    using System;
    using System.Threading.Tasks;
```

1.  기존 코드 대신에 다음 코드를 입력하여 새 **Program** 클래스를 만듭니다.

```
    public class Program
    {
    }
``` 

1.  **Program** 클래스 내에서 다음 코드 줄을 입력하여 **blobServiceEndpoint** 라는 새 문자열 상수를 만듭니다.

```
    private const string blobServiceEndpoint = "";
```

1.  이 랩의 앞에서 기록한 스토리지 계정의 **기본 엔드포인트 Blob Service ** 로 값을 설정하여 **blobServiceEndpoint** 문자열 상수를 업데이트합니다.

1.  **Program** 클래스 내에서 다음 코드 줄을 입력하여 **storageAccountName** 이 라는 새 문자열 상수를 만듭니다.

```
    private const string storageAccountName = "";
```

1.  이전에 랩에서 기록한 스토리지 계정의 **스토리지 계정 이름** 으로 값을 설정하여 **storageAccountName** 문자열 상수를 업데이트합니다.

1.  **Program** 클래스에서 다음 코드 줄을 입력하여 **storageAccountKey** 이 라는 새 문자열 상수를 만듭니다.

```
    private const string storageAccountKey = "";
```

1.  해당 랩 앞에서 기록한 스토리지 계정의 **키** 로 값을 설정하여 **storageAccountKey** 문자열 상수를 업데이트합니다.

1.  **Program** 클래스에서 다음 코드 줄을 입력하여 새 비동기 **Main** 메서드를 만듭니다.

```
    public static async Task Main(string[] args)
    {
    }
```

1.  이제 다음을 포함하는 **Program.cs** 파일을 관찰하세요.

```
    using Azure.Storage;
    using Azure.Storage.Blobs;
    using Azure.Storage.Blobs.Models;
    using System;
    using System.Threading.Tasks;

    public class Program
    {
        private const string blobServiceEndpoint = "<primary-blob-service-endpoint>";
        private const string storageAccountName = "<storage-account-name>";
        private const string storageAccountKey = "<key>";

        public static async Task Main(string[] args)
        {
        }
    }
```

#### 작업 3: Azure Storage Blob 서비스 엔드포인트에 연결

1.  **Main** 메서드에서 다음 코드 줄을 추가하여 **storageAccountName** 및 **storageAccountKey** 상수를 생성자 매개 변수로 사용하여 **StorageSharedKeyCredential** 자격 증명 클래스의 새 인스턴스를 만듭니다.

```
    StorageSharedKeyCredential accountCredentials = new StorageSharedKeyCredential(storageAccountName, storageAccountKey);
```

1.  **Main** 메서드에서 다음 코드 줄을 추가하여 **BlobServiceEndpoint** 상수 및 *accountCredentials* 변수를 생성자 매개 변수로 사용하여 **BlobServiceClient** 클래스의 새 인스턴스를 만듭니다.

```
    BlobServiceClient serviceClient = new BlobServiceClient(new Uri(blobServiceEndpoint), accountCredentials);
```

1.  **Main** 메서드에서 다음 코드 줄을 추가하여 **BlobServiceClient** 클래스의 **GetAccountInfoAsync** 메서드를 호출하여 서비스에서 계정 메타데이터를 검색합니다.     

```
    AccountInfo info = await serviceClient.GetAccountInfoAsync();
```
    
1.  **Main** 메서드 내에서 다음 코드 줄을 추가하여 콘솔에 소개 메시지를 렌더링합니다.

```
    await Console.Out.WriteLineAsync($"Connected to Azure Storage Account");
```
    
1.  **Main** 메서드 내에서 다음 코드 줄을 추가하여 스토리지 계정 이름을 렌더링합니다.

```
    await Console.Out.WriteLineAsync($"Account name:\t{storageAccountName}");
```
    
1.  **Main** 메서드 내에서 다음 코드 줄을 추가하여 스토리지 계정 형식을 렌더링합니다:

```
    await Console.Out.WriteLineAsync($"Account kind:\t{info?.AccountKind}");
```
    
1.  **Main** 메서드에서 다음 코드 줄을 추가하여 스토리지 계정에 대해 현재 선택된 SKU(Stock Keeping Unit)를 렌더링합니다.

```
    await Console.Out.WriteLineAsync($"Account sku:\t{info?.SkuName}");
```

1.  이제 다음을 포함해야 하는 **Main** 메서드를 살펴봅니다.

```
    public static async Task Main(string[] args)
    {
        StorageSharedKeyCredential accountCredentials = new StorageSharedKeyCredential(storageAccountName, storageAccountKey);	

        BlobServiceClient serviceClient = new BlobServiceClient(new Uri(blobServiceEndpoint), accountCredentials);

        AccountInfo info = await serviceClient.GetAccountInfoAsync();

        await Console.Out.WriteLineAsync($"Connected to Azure Storage Account");
        await Console.Out.WriteLineAsync($"Account name:\t{storageAccountName}");
        await Console.Out.WriteLineAsync($"Account kind:\t{info?.AccountKind}");
        await Console.Out.WriteLineAsync($"Account sku:\t{info?.SkuName}");
    }
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 탐색기 창의 바로 가기 메뉴를 마우스 오른쪽 단추로 클릭하거나 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\03\\Solution\\BlobManager** 폴더에 있는 **Program.cs** 파일을 검토합니다.

1.  현재 실행 중인 콘솔 애플리케이션의 출력을 살펴봅니다. 출력에는 서비스에서 검색된 스토리지 계정에 대한 메타데이터가 포함되어 있습니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 4: 기존 컨테이너 열거

1.  **Program** 클래스에서 다음 코드를 입력하여 비동기이고 단일 **BlobServiceClient** 매개 변수 유형이 있는 **EnumerateContainersAsync** 라는 새 **private static** 메서드를 만듭니다.

```
    private static async Task EnumerateContainersAsync(BlobServiceClient client)
    {        
    }
```

1.  **EnumerateContainersAsyn** 메서드에서 다음 코드를 입력하여 **BlobServiceClient** 클래스의 **GetBlobContainersAsync** 메서드 호출 결과를 반복하는 비동기 **foreach** 루프를 만듭니다.

```
    await foreach (BlobContainerItem container in client.GetBlobContainersAsync())
    {
    }
```

1.  **foreach** 루프 내에서 다음 코드를 입력하여 각 컨테이너의 이름을 인쇄합니다.

```
    await Console.Out.WriteLineAsync($"Container:\t{container.Name}");
```

1.  이제 다음을 포함해야 하는 **EnumerateContainersAsync** 메서드를 관찰합니다. 

```
    private static async Task EnumerateContainersAsync(BlobServiceClient client)
    {        
        await foreach (BlobContainerItem container in client.GetBlobContainersAsync())
        {
            await Console.Out.WriteLineAsync($"Container:\t{container.Name}");
        }
    }
```

1.  **Mai** 메서드에서 다음 코드를 입력 하여 **EnumerateContainersAsync** 메서드를 호출하여 *serviceClient* 변수를 매개 변수로  전달합니다.   

```
    await EnumerateContainersAsync(serviceClient);
```

1.  이제 다음을 포함해야 하는 **기본** 메서드를 살펴봅니다.

```
    public static async Task Main(string[] args)
    {
        \\간결성을 위해 제거된 기존 코드
        
        await EnumerateContainersAsync(serviceClient);
    }
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 컨텍스트 메뉴에 액세스하거나 Explorer 창을 마우스 오른쪽 단추 또는 바로가기 메뉴를 클릭한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\03\\Solution\\BlobManager** 폴더에 있는 **Program.cs** 파일을 검토합니다.

1.  현재 실행 중인 콘솔 애플리케이션의 출력을 살펴봅니다. 업데이트된 출력에는 계정의 모든 기존 컨테이너 목록이 포함됩니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 검토

이 연습에서는 Azure Storage SDK를 사용하여 기존 컨테이너에 액세스했습니다. 

### 연습 4: .NET SDK를 사용하여 BLOB URI(Uniform Resource Identifier)를 검색합니다.

#### 작업 1: SDK를 사용하여 기존 컨테이너의 Blob을 열거합니다.

1.  **Program** 클래스에서 다음 코드를 입력하여 비동기이며 **BlobServiceClient**와 **문자열** 이 라는 두 개의 매개 변수 유형이 있는 **EnumerateBlobsAsync** 라는 새 **private static** 메서드를 만듭니다.

```
    private static async Task EnumerateBlobsAsync(BlobServiceClient client, string containerName)
    {      
    }
```

1.  **EnumerateContainersAsync]** 메서드에서 다음 코드를 입력하여 **BlobServiceClient** 클래스의 **GetBlobContainerClient** 메서드를 사용하여 **BlobContainerClient** 클래스의 새 인스턴스를 **containerName** 매개 변수에 전달합니다.

```
    BlobContainerClient container = client.GetBlobContainerClient(containerName);
```

1.   **EnumerateBlobsAsync** 메서드에서 다음 코드를 입력하여 열거될 컨테이너의 이름을 렌더링합니다. 

```
    await Console.Out.WriteLineAsync($"Searching:\t{container.Name}");
```

1.  **EnumerateBlobsAsync** 메서드에서 다음 코드를 입력하여 **BlobContainerClient** 클래스의 **GetBlobsAsync** 메서드 호출 결과를 반복하는 비동기 **foreach** 루프를 만듭니다.

```
    await foreach (BlobItem blob in container.GetBlobsAsync())
    {        
    }
```

1.  **foreach** 루프 내에서 다음 코드를 입력하여 각 Blob의 이름을 인쇄합니다. 

```
     await Console.Out.WriteLineAsync($"Existing Blob:\t{blob.Name}");
```

1.  이제 다음을 포함해야 하는 **EnumerateBlobsAsync** 메서드를 준수하세요.

```
    private static async Task EnumerateBlobsAsync(BlobServiceClient client, string containerName)
    {      
        BlobContainerClient container = client.GetBlobContainerClient(containerName);
        
        await Console.Out.WriteLineAsync($"Searching:\t{container.Name}");
        
        await foreach (BlobItem blob in container.GetBlobsAsync())
        {        
             await Console.Out.WriteLineAsync($"Existing Blob:\t{blob.Name}");
        }
    }
```

1.  **Main** 메서드에서 메서드 끝에 다음 코드를 입력하여 **래스터 그래픽** 값을 가진 *existingContainerName* 이 라는 변수를 만듭니다.

```
    string existingContainerName = "raster-graphics";
```

1.  **기본** 메서드에서 다음 코드를 입력하여 **EnumerateBlobsAsync** 메서드를 호출하여 *serviceClient* 및 *existingContainerName* 변수를 매개 변수로 전달합니다.

```
    await EnumerateBlobsAsync(serviceClient, existingContainerName);
```

1.  이제 다음을 포함해야 하는 **Main** 메서드를 살펴봅니다.

```
    public static async Task Main(string[] args)
    {
        \\간결성을 위해 제거된 기존 코드
        
        await EnumerateContainersAsync(serviceClient);

        string existingContainerName = "raster-graphics";
        await EnumerateBlobsAsync(serviceClient, existingContainerName);
    }
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 탐색기 창의 바로 가기 메뉴를 마우스 오른쪽 단추로 클릭하거나 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\03\\Solution\\BlobManager** 폴더에 있는 **Program.cs** 파일을 검토합니다.

1.  현재 실행 중인 콘솔 애플리케이션의 출력을 살펴봅니다. 업데이트된 출력에는 기존 컨테이너 및 BLOB에 대한 메타데이터가 포함됩니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 2: SDK를 사용하여 새 컨테이너 만들기

1.  **Program** 클래스에서 다음 코드를 입력하여 비동기인 **BlobServiceClient** 및 **string** 이 라는 두 개의 매개 변수 유형이 있는 **GetContainerAsync** 라는 새 **private static** 메서드를 만듭니다:

```
    private static async Task<BlobContainerClient> GetContainerAsync(BlobServiceClient client, string containerName)
    {      
    }
```

1.  **GetContainerAsync** 메서드에서 다음 코드를 입력하여 **BlobServiceClient** 클래스의 **GetBlobContainerClient** 메서드를 사용하여 **BlobContainerClient** 클래스의 새 인스턴스를 **containerName** 매개 변수에 전달합니다.

```
    BlobContainerClient container = client.GetBlobContainerClient(containerName);
```

1.  **GetContainerAsync** 메서드에서 다음 코드를 입력하여 **BlobContainerClient** 클래스의 **CreateIfNotExistsAsync** 메서드를 호출합니다.

```
    await container.CreateIfNotExistsAsync(PublicAccessType.Blob);
```

1.  **GetContainerAsync** 메서드에서 다음 코드를 입력하여 잠재적으로 만들어진 컨테이너의 이름을 렌더링합니다.

```
    await Console.Out.WriteLineAsync($"New Container:\t{container.Name}");
```

1.  **GetContainerAsync** 메서드에서 다음 코드를 입력하여 **GetContainerAsync** 메서드의 결과로 **컨테이너** 라는 **BlobContainerClient** 클래스의 인스턴스를 반환합니다.

```
    return container;
```  

1.  이제 다음을 포함해야 하는 **GetContainerAsync** 메서드를 살펴봅니다.

```
    private static async Task<BlobContainerClient> GetContainerAsync(BlobServiceClient client, string containerName)
    {      
        BlobContainerClient container = client.GetBlobContainerClient(containerName);
        
        await container.CreateIfNotExistsAsync();
        
        await Console.Out.WriteLineAsync($"New Container:\t{container.Name}");
        
        return container;
    }
```

1.  **기본** 메서드에서 메서드 끝에 다음 코드를 입력하여 **벡터 그래픽** 값을 가진 *newContainerName* 이 라는 변수를 만듭니다.

```
    string newContainerName = "vector-graphics";
```

1.  **Main** 메서드에서 다음 코드를 입력하여 **GetContainerAsync** 메서드를 호출하고 *serviceClient* 및 *newContainerName* 변수를 매개 변수로 전달하고 **BlobContainerClient** 형식의 *containerClient* 라는 변수에 결과를 저장합니다.

```
    BlobContainerClient containerClient = await GetContainerAsync(serviceClient, newContainerName);
```

1.  이제 다음을 포함해야 하는 **Main** 메서드를 살펴봅니다.

```
    public static async Task Main(string[] args)
    {
        \\간결성을 위해 제거된 기존 코드
        
        await EnumerateContainersAsync(serviceClient);

        string existingContainerName = "raster-graphics";
        await EnumerateBlobsAsync(serviceClient, existingContainerName);
        
        string newContainerName = "vector-graphics";
        BlobContainerClient containerClient = await GetContainerAsync(serviceClient, newContainerName);
    }
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 탐색기 창의 바로 가기 메뉴를 마우스 오른쪽 단추로 클릭하거나 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\03\\Solution\\BlobManager** 폴더에 있는 **Program.cs** 파일을 검토합니다.

1.  현재 실행 중인 콘솔 애플리케이션의 출력을 살펴봅니다. 업데이트된 출력에는 기존 컨테이너 및 BLOB에 대한 메타데이터가 포함됩니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 3: 포털을 사용하여 새 BLOB 업로드

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서, 이 랩의 앞에서 만든 **StorageMedia** 리소스 그룹을 찾아 선택합니다.

1.  **StorageMedia** 블레이드에서 이 랩의 앞에서 만든 **mediastor*[yourname]*** 스토리지 계정을 선택합니다.

1.  **스토리지 계정** 블레이드에서 **Blob Service** 섹션에 있는 **컨테이너** 링크를 선택합니다.

1.  **컨테이너** 섹션에서 새로 만든 **vector-graphics** 컨테이너를 선택합니다.

1.	**컨테이너** 블레이드에서 **업로드** 를 선택합니다.

1.	**BLOB 업로드** 창에서 다음 작업을 수행합니다.

    1.  **파일** 섹션에서 **폴더** 아이콘을 선택합니다.

    1.  **파일 탐색기** 창에서 **Allfiles (F):\\Allfiles\\Labs\\03\\Starter\\Images** 로 이동하여 **graph.svg** 파일을 선택하고 **열기** 를 선택합니다.

    1.  **파일이 이미 있는 경우 덮어쓰기** 확인란이 선택되어 있는지 확인하고, **업로드** 를 선택합니다. 
    
    > **참고**: 이 랩을 계속하기 전에 Blob이 업로드될 때까지 기다립니다.

#### 작업 4: SDK를 사용하여 BLOB URI에 액세스

1.  **Program** 클래스에서 다음 코드를 입력하여 비동기이며 **BlobContainerClient** 및 **문자열** 이 라는 두 개의 매개 변수 유형이 있는 **GetBlobAsync** 라는 새 **private static** 메서드를 만듭니다.

```
    private static async Task<BlobClient> GetBlobAsync(BlobContainerClient client, string blobName)
    {      
    }
```

1.  **GetBlobAsync** 메서드에서 다음 코드를 입력하여 **BlobContainerClient** 클래스의 **GetBlobClient** 메서드를 사용하여 **BlobName** 매개 변수를 전달하여 **BlobClient** 클래스의 새 인스턴스를 가져옵니다.

```
    BlobClient blob = client.GetBlobClient(blobName);
```

1.  **GetBlobAsync** 메서드에서 참조된 Blob의 이름을 렌더링하려면 다음 코드를 입력합니다.

```
    await Console.Out.WriteLineAsync($"Blob Found:\t{blob.Name}");
```

1.  **GetBlobAsync** 메서드에서 다음 코드를 입력하여 **GetBlobAsync** 메서드의 결과로 **Blob** 이 라는 **BlobClient** 클래스의 인스턴스를 반환합니다.

```
    return blob;
```

1.  이제 다음을 포함해야 하는 **GetBlobAsync** 메서드를 확인 합니다.

```
    private static async Task<BlobClient> GetBlobAsync(BlobContainerClient client, string blobName)
    {      
        BlobClient blob = client.GetBlobClient(blobName);
        await Console.Out.WriteLineAsync($"Blob Found:\t{blob.Name}");
        return blob;
    }
```

1.  **Main** 메서드에서 메서드 끝에 다음 코드를 입력하여 **graph.svg** 값을 가진 *uploadedBlobName* 라는 이름의 변수를 만듭니다.

```
    string uploadedBlobName = "graph.svg";
```

1.  **Main** 메서드에서 다음 코드를 입력하여 **GetBlobAsync** 메서드를 호출하고 *containerClient* 및 *uploadedBlobName* 변수를 매개 변수로 전달하고 *BlobClient* 형식이라는 **blobClient** 변수에 결과를 저장합니다.

```
    BlobClient blobClient = await GetBlobAsync(containerClient, uploadedBlobName);
```

1.  **Main** 메서드에서 **blobClient** 변수의 *Uri* 속성을 렌더링하는 메서드의 끝에 다음 코드를 입력합니다.

```
    await Console.Out.WriteLineAsync($"Blob Url:\t{blobClient.Uri}");
```

1.  이제 다음을 포함해야 하는 **Main** 메서드를 살펴봅니다.

```
    public static async Task Main(string[] args)
    {
        \\간결성을 위해 제거된 기존 코드
        
        await EnumerateContainersAsync(serviceClient);

        string existingContainerName = "raster-graphics";
        await EnumerateBlobsAsync(serviceClient, existingContainerName);
        
        string newContainerName = "vector-graphics";
        BlobContainerClient containerClient = await GetContainerAsync(serviceClient, newContainerName);
        
        string uploadedBlobName = "graph.svg";
        BlobClient blobClient = await GetBlobAsync(containerClient, uploadedBlobName);

        await Console.Out.WriteLineAsync($"Blob Url:\t{blobClient.Uri}");
    }
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 탐색기 창의 바로 가기 메뉴를 마우스 오른쪽 단추로 클릭하거나 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\03\\Solution\\BlobManager** 폴더에 있는 **Program.cs** 파일을 검토합니다.

1.  현재 실행 중인 콘솔 애플리케이션의 출력을 살펴봅니다. 업데이트된 출력에는 BLOB에 온라인으로 액세스할 수 있는 최종 URL이 포함됩니다. 이 URL의 값을 기록하여 이 랩의 후반부에서 사용합니다.

    > **참고**: URL은 다음 문자열 **https://mediastor*[yourname]*.blob.core.windows.net/vector-graphics/graph.svg** 와 유사할 수 있습니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 5: 브라우저를 사용하여 URI 테스트

1.  작업 표시줄에서 **Microsoft Edge** 아이콘을 오른쪽 버튼으로 클릭하거나 바로 가기 메뉴를 활성화한 다음 **새 창** 을 선택합니다.

1.  새 브라우저 창에서 이 랩 앞부분의 lob을 복사한 URL로 이동합니다.

1.  이제 브라우저 창에서 SVG(확장성 있는 벡터 그래픽) 파일을 확인할 수 있습니다.

#### 검토

이 연습에서는 저장소 SDK를 사용하여 컨테이너및 관리 BLOB을 만들었습니다. 

### 연습 5: 구독 정리 

#### 작업 1: Azure Cloud Shell 열기 및 리소스 그룹 나열

1.  Azure Portal의 탐색 창에서 **Cloud Shell** 아이콘을 선택하여 새 셸 인스턴스를 엽니다.

    > **참고**: **Cloud Shell** 아이콘은 초과(\>) 기호와 밑줄 문자(\_)로 표시됩니다.

1.  구독을 사용하여 Cloud Shell을 처음으로 여는 경우, 처음 사용할 경우에만 **Azure Cloud Shell 시작 마법사** 를 사용하여 Cloud Shell를 구성할 수 있습니다. 마법사에서 다음 작업을 수행합니다.
    
    1.  대화 박스는 셸을 사용하여 시작할 새 스토리지 계정을 만들라는 메시지를 표시합니다. 기본 설정을 수락하고 **스토리지 만들기** 를 선택합니다. 

    > **참고**: 랩으로 진행하기 전에 Cloud Shell이 초기 설치 절차를 완료할 때까지 기다립니다. Cloud Shell의 구성 옵션이 나타나지 않는 경우 이 과정의 랩에서 기존 구독을 사용하고 있기 때문일 가능성이 높습니다. 랩은 새 구독을 사용한다는 가정 하에서 작성됩니다.

1.  포털의 **Cloud Shell** 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 구독의 모든 리소스 그룹을 나열합니다.

```
    az group list
```

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 눌러 리소스 그룹을 삭제하는 데 사용할 수 있는 명령 목록을 가져옵니다.

```
    az group delete --help
```

#### 작업 2: 리소스 그룹 삭제

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 눌러 **StorageMedia** 리소스 그룹을 삭제합니다.

```
    az group delete --name StorageMedia --no-wait --yes
```
    
1.  포털에서 Cloud Shell 창을 닫습니다.

#### 작업 3: 활성 애플리케이션 닫기

1.     현재 실행 중인 Microsoft Edge 애플리케이션.

#### 검토

이 연습에서는 이 랩에 사용된 리소스 그룹을 제거하여 구독을 정리했습니다.
