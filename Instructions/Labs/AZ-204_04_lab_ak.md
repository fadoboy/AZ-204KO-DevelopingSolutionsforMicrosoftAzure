---
lab:
    title: '랩: Azure Cosmos DB를 사용하여 NoSQL 데이터 솔루션 구축'
    az204Module: '모듈 04: Cosmos DB 스토리지를 사용하는 솔루션 개발'
    type: 'Answer Key'
---

# 랩: polyglot 데이터 솔루션 구축
# 학생 랩 Answer Key

## Microsoft Azure 사용자 인터페이스

Microsoft 클라우드 도구의 동적 특성을 감안할 때 이 교육 콘텐츠의 개발 후 Azure UI 변경 사항이 발생할 수 있습니다. 이러한 변경으로 인해 랩 지침 및 단계가 올바르게 일치하지 않을 수 있습니다.

Microsoft는 커뮤니티에서 주목해야 할 변경 사항이 있을 때 이 학습 과정을 업데이트합니다. 그러나 클라우드 업데이트가 자주 이루어지기 때문에 이 학습 콘텐츠가 업데이트되기 전에 UI가 변경될 수 있습니다. **이 경우 변경 사항에 적응하고 필요에 따라 랩에서 작업합니다.**

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

-   Visual Studio Code

### 연습 1: Azure에서 데이터베이스 리소스 만들기

#### 작업 1: Azure Portal 열기

1.  작업 표시줄에서 **Microsoft Edge** 아이콘을 선택합니다.

1.  열린 브라우저 창에서 Azure Portal([portal.azure.com](https://portal.azure.com))로 이동합니다.

1.  Microsoft 계정의 이메일 주소를 입력한 다음 **다음** 을 선택합니다.

1.  Microsoft 계정의 암호를 입력한 다음 **로그인** 을 선택합니다.

    > **참고**: Azure Portal에 처음 로그인하는 경우 포털 둘러보기 기능이 제공됩니다. 둘러보기를 건너뛰고 포털을 사용하려면 **시작하기** 를 선택합니다.

#### 작업 2: Azure SQL Database 서버 리소스 만들기

1.  Azure Portal 탐색 창에서 **모든 서비스** 를 선택합니다.

1.  **모든 서비스** 블레이드에서 **SQL Server** 를 선택합니다.

1.  **SQL Server** 블레이드에서 SQL 서버 인스턴스 목록을 확인한다.

1.  **SQL Server** 블레이드에서 **추가** 를 선택합니다.

1.  **SQL Database 서버 만들기** 블레이드에서 **기본**, **네트워킹** 및 **추가 설정** 과 같은 블레이드의 탭을 살펴봅니다.

    > **참고**: 각 탭은 새 Azure SQL Database 서버를 만드는 워크플로의 단계를 나타냅니다. 언제든지 **검토 + 만들기** 를 선택하여 나머지 탭을 건너뛸 수 있습니다.

    1.  **기본** 탭에서 다음 작업을 수행합니다.
    
    1.  **구독** 드롭다운 목록을 기본값으로 둡니다.
    
    1.  **리소스 그룹** 섹션에서 **새로 만들기** 를 선택하고 **PolyglotData** 를 입력한 다음 **확인** 을 선택합니다.
    
    1.  **서버 이름** 텍스트 상자에 **polysqlsrvr*[yourname]*** 을/를 입력합니다.
    
    1.  **위치** 드롭다운 목록에서 **(US) 미국 동부** 를 선택합니다.
    
    1.  **서버 관리자 로그인** 텍스트 상자에 **testuser** 를 입력합니다.
    
    1.  **암호** 텍스트 상자에 **TestPa55w.rd** 를 입력합니다.
    
    1.  **암호 확인** 텍스트 상자에 **TestPa55w.rd** 를 다시 입력합니다.

    1.  **다음: 네트워킹**.

1.  **네트워킹** 탭에서 다음 작업을 수행합니다.

    1.  **Azure 서비스 및 리소스가 이 서버에 액세스할 수 있도록 허용** 섹션에서 **예** 를 선택합니다.
    
    1.  **검토 + 만들기** 를 선택합니다.

1.  **검토 + 만들기** 탭에서 이전 단계에서 선택한 옵션을 검토합니다.

1.  **만들기** 를 선택하여 지정한 구성으로 Azure SQL Database 서버를 만듭니다.

    > **참고**: 지금은 Azure SQL 논리 서버만 만듭니다. 나중에 랩에서 Azure SQL 데이터베이스 인스턴스를 만들 것입니다.

    > **참고**: 이 랩을 진행하기 전에 만들기 작업이 완료될 때까지 기다립니다.

#### 작업 3: Azure Cosmos DB 계정 리소스 만들기

1.  Azure Portal 탐색 창에서 **모든 서비스** 를 선택합니다.

1.  **모든 서비스** 블레이드에서 **Azure Cosmos DB** 를 선택합니다.

1.  **Azure Cosmos DB** 블레이드에서 Azure Cosmos DB 인스턴스 목록을 찾습니다.

1.  **Azure Cosmos DB** 블레이드에서 **추가** 를 선택합니다.

1.  **Azure Cosmos DB 계정 만들기** 블레이드에서 **기본**, **네트워크** 및 **태그** 와 같은 블레이드 탭을 살펴봅니다.

    > **참고**: 각 탭은 새 Azure Cosmos DB 계정을 만드는 워크플로의 단계를 나타냅니다. 언제든지 **검토 + 만들기** 를 선택하여 나머지 탭을 건너뛸 수 있습니다.

1.  **기본** 탭에서 다음 작업을 수행합니다.
    
    1.  **구독** 목록을 기본값으로 둡니다.
    
    1.  **리소스 그룹** 섹션의 목록에서 **PolyglotData** 를 선택합니다.
    
    1.  **계정 이름** 텍스트 상자에 **polycosmos*[yourname]*** 을 입력합니다.
    
    1.  **API** 드롭다운 목록에서 **코어(SQL)** 를 선택합니다.

    1.  **Notebooks (Preview)** 섹션에서 **Off** 을 선택합니다.
    
    1.  **위치** 드롭다운 목록에서 **(US) 미국 동부** 지역을 선택합니다.
    
    1.  **Apply Free Tier Discount** 섹션에서 **Do Not Apply** 을 선택합니다.
    
    1.  **Account Type** 섹션에서 **Non-Production** 을 선택합니다.
    
    1.  **지리적 중복성** 섹션에서 **사용 안 함** 옵션을 선택합니다.
    
    1.  **다중 지역 쓰기** 섹션에서 **사용 안 함** 을 선택합니다.
    
    1.  **검토 + 만들기** 를 선택합니다.

1.  **검토 + 만들기** 탭에서 이전 단계에서 선택한 옵션을 검토합니다.

1.  **만들기** 를 선택하여 지정한 구성으로 Azure Cosmos DB 계정을 만듭니다.

    > **참고**: 이 랩을 진행하기 전에 만들기 작업이 완료될 때까지 기다립니다.

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩의 앞부분에서 만든 **PolyglotData** 리소스 그룹을 찾아 선택합니다.

1.  **PolyglotData** 블레이드에서 이 랩의 앞부분에서 만든 **polycosmos*[yourname]*** Azure Cosmos DB 계정을 선택합니다.

1.  **Azure Cosmos DB 계정** 블레이드에서 **설정** 섹션을 찾아 **키** 링크를 선택합니다.

1.  키 창에서 **기본 연결 문자열** 텍스트 상자의 값을 기록합니다. 나중에 이 랩에서 이 값을 사용하게 됩니다.

#### 작업 4: Azure Storage 계정 리소스 만들기

1.  Azure Portal 탐색 창에서 **모든 서비스** 를 선택합니다.

1.  **모든 서비스** 블레이드에서 **스토리지 계정** 을 선택합니다.

1.  **스토리지 계정** 블레이드에서 스토리지 인스턴스 목록을 확인합니다.

1.  **스토리지 계정** 블레이드에서 **추가** 를 선택합니다.

1.  **스토리지 계정 만들기** 블레이드에서 **기본**, **고급** 및 **태그** 와 같은 블레이드 탭을 살펴봅니다.

    > **참고**: 각 탭은 새 Azure Storage 계정을 만드는 워크플로의 단계를 나타냅니다. 언제든지 **검토 + 만들기** 를 선택하여 나머지 탭을 건너뛸 수 있습니다.

1.  **기본** 탭에서 다음 작업을 수행합니다.
    
    1.  **구독** 목록을 기본값으로 둡니다.
    
    1.  **리소스 그룹** 섹션의 목록에서 **PolyglotData** 를 선택합니다.
    
    1.  **스토리지 계정 이름** 텍스트 상자에 **polystor*[yourname]*** 을 입력합니다.
    
    1.  **위치** 드롭다운 목록에서 **(US)미국 동부** 지역을 선택합니다.
    
    1.  **성능** 섹션에서 **표준** 을 선택합니다.
    
    1.  **계정 종류** 드롭다운 목록에서 **StorageV2(범용 v2)** 를 선택합니다.
    
    1.  **복제** 드롭다운 목록에서 **LRS(로컬 중복 스토리지)** 를 선택합니다.
    
    1.  **액세스 계층(기본값)** 섹션에서 **핫** 이 선택되어 있는지 확인합니다.
    
    1.  **검토 + 만들기** 를 선택합니다.

1.  **검토 + 만들기** 탭에서 이전 단계에서 선택한 옵션을 검토합니다.

1.  지정된 구성을 사용하여 스토리지 계정을 만들려면 **만들기** 를 선택합니다.

    > **참고**: 이 랩을 진행하기 전에 만들기 작업이 완료될 때까지 기다립니다.

#### 복습

이 연습에서는 다중저장소 데이터 솔루션에 필요한 모든 Azure 리소스를 만들었습니다.

### 연습 2: 데이터 가져오기 및 유효성 검사

#### 작업 1: 이미지 Blob 업로드

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩의 앞부분에서 만든 **PolyglotData** 리소스 그룹을 찾아 선택합니다.

1.  **PolyglotData** 블레이드에서 이 랩의 앞부분에서 만든 **polystor*[yourname]*** 스토리지 계정을 선택합니다.

1.  **스토리지 계정** 블레이드에서 **Blob 서비스** 섹션에 있는 **컨테이너** 링크를 선택합니다.

1.  **컨테이너** 섹션에서 **+ 컨테이너** 를 선택합니다.

1.  **새 컨테이너** 에서 다음 작업:
    
    1.  **이름** 텍스트 상자에 **images** 를 입력합니다.
    
    1.  **공용 액세스 수준** 드롭다운 목록에서 **Blob(Blob 에 대한 익명 읽기 전용 액세스)** 을 선택합니다.
    
    1.  **확인** 을 선택합니다.

1.  **컨테이너** 섹션으로 돌아가서 새로 만든 **이미지** 컨테이너를 선택합니다.

1.  **컨테이너** 블레이드에서 **설정** 섹션을 찾은 다음 **속성** 링크를 선택합니다.

1.  속성 창에서 **URL** 텍스트 상자의 값을 기록합니다. 나중에 이 랩에서 이 값을 사용하게 됩니다.

1.  블레이드에서 **개요** 링크를 찾아 선택합니다.

1.  블레이드에서 **업로드** 를 선택합니다.

1.  **Blob 업로드** 팝업 창에서 다음 작업을 수행합니다.
    
    1.  **파일** 섹션에서 **폴더** 아이콘을 선택합니다.
    
    1.  **파일 탐색기** 창에서 **Allfiles (F):\\Allfiles\\Labs\\04\\Starter\\Images** 로 이동하여 42개의 **jpg** 이미지 파일을 모두 선택하고 **열기** 를 선택합니다.
    
    1.  **파일이 이미 있는 경우 덮어쓰기** 가 선택되어 있는지 확인하고 **업로드** 를 선택합니다.

    > **참고**: 이 랩으로 계속하기 전에 모든 Blob이 업로드할 때까지 기다립니다.

#### 작업 2: SQL .bacpac 파일 업로드

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩의 앞부분에서 만든 **PolyglotData** 리소스 그룹을 찾아 선택합니다.

1.  **PolyglotData** 블레이드에서 이 랩의 앞부분에서 만든 **polystor*[yourname]*** 스토리지 계정을 선택합니다.

1.  **스토리지 계정** 블레이드에서 **Blob 서비스** 섹션에 있는 **컨테이너** 링크를 선택합니다.

1.  **컨테이너** 섹션에서 **+ 컨테이너** 를 선택합니다.

1.  **새 컨테이너** 팝업에서 다음 작업을 수행합니다.
    
    1.  **이름** 텍스트 상자에 **databases** 를 입력합니다.
    
    1.  **공용 액세스 수준** 드롭다운 목록에서 **프라이빗(익명 액세스 없음)** 를 선택합니다.
    
    1.  **확인** 을 선택합니다.

1.  **컨테이너** 섹션으로 돌아가서 새로 만든 **databases** 컨테이너를 선택합니다.

1.  **컨테이너** 블레이드에서 **업로드** 를 선택합니다.

1.  **Blob 업로드** 팝업 창에서 다음 작업을 수행합니다.
    
    1.  **파일** 섹션에서 **폴더** 아이콘을 선택합니다.
    
    1.  **파일 탐색기** 창에서 **Allfiles (F):\\Allfiles\\Labs\\04\\Starter** 로 이동하여 **AdventureWorks.bacpac** 파일을 선택하고 **열기** 를 선택합니다.
    
    1.  **파일이 이미 있는 경우 덮어쓰기** 가 선택되어 있는지 확인하고 **업로드** 를 선택합니다.

    > **참고**: 이 랩을 계속하기 전에 Blob이 업로드될 때까지 기다립니다.

#### 작업 3: SQL Database 가져오기

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩의 앞부분에서 만든 **PolyglotData** 리소스 그룹을 찾아 선택합니다.

1.  **PolyglotData** 블레이드에서 이 랩의 앞부분에서 만든 **polysqlsrvr*[yourname]*** SQL Server를 선택합니다.

1.  **SQL 서버** 블레이드에서 **데이터베이스 가져오기** 를 선택합니다.

1.  **데이터베이스 가져오기** 블레이드에서 다음 작업을 수행합니다.

    1.  **구독** 목록을 기본값으로 둡니다.

    1.  **스토리지** 옵션을 선택합니다.

    1.  **스토리지 계정** 블레이드에서 이 랩의 앞부분에서 만든 **polystor*[yourname]*** 스토리지 계정을 선택합니다. 

    1.  **컨테이너** 블레이드에서 이 랩의 앞부분에서 만든 **databases** 컨테이너를 선택합니다. 

    1.  **컨테이너** 블레이드에서 이 랩의 앞부분에서 만든 **AdventureWorks.bacpac** Blob을 선택한 다음 **선택** 을 선택하여 블레이드를 닫습니다.

    1.  **데이터베이스 가져오기** 블레이드로 돌아가서 **가격 책정 계층** 옵션을 기본값으로 둡니다.

    1.  **데이터베이스 이름** 텍스트 상자에 **AdventureWorks** 를 입력합니다.

    1.  **데이터 정렬** 텍스트 상자를 기본값으로 둡니다.

    1.  **서버 관리자 로그인** 텍스트 상자에 **testuser** 를 입력합니다.
    
    1.  **암호** 텍스트 상자에 **TestPa55w.rd** 를 입력합니다.
    
    1.  **확인** 을 선택합니다.

    > **참고**: 이 랩을 계속 실행하기 전에 데이터베이스가 만들어질 때까지 기다립니다.

#### 작업 4: 가져온 SQL Database 사용

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩의 앞부분에서 만든 **PolyglotData** 리소스 그룹을 찾아 선택합니다.

1.  **PolyglotData** 블레이드에서 이 랩의 앞부분에서 만든 **polysqlsrvr*[yourname]*** SQL Server를 선택합니다.

1.  **SQL 서버** 블레이드에서 **보안** 섹션을 찾아 **방화벽 및 가상 네트워크** 링크를 선택합니다.

1.  벙화벽 및 가상 네트워크 창에서 다음 작업을 수행합니다.

    1.  **클라이언트 IP 추가** 를 선택합니다.
    
    1.  **저장** 을 선택합니다.

    1.  **성공!** 확인 대화 상자에서 **확인** 을 선택합니다.

    > **참고**: 이 단계를 통해 로컬 컴퓨터가 이 서버와 연결된 데이터베이스에 액세스할 수 있습니다.

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩의 앞부분에서 만든 **PolyglotData** 리소스 그룹을 찾아 선택합니다.

1.  **PolyglotData** 블레이드에서 이 랩의 초반에 만든 **AdventureWorks** SQL 데이터베이스를 선택합니다.

1.  **SQL 데이터베이스** 블레이드에서 **설정** 섹션을 찾은 다음 **연결 문자열** 링크를 선택합니다.

1.  연결 문자열 창에서 **ADO.NET(SQL 인증)** 텍스트 상자의 값을 기록합니다. 나중에 이 랩에서 이 값을 사용하게 됩니다.

1.  다음 작업을 수행하여 기록한 연결 문자열을 업데이트합니다.

    1.  연결 문자열 내에서 *your_username* 자리 표시자를 찾아 **testuser** 로 바꿉니다.

    1.  연결 문자열 내에서 *your_password* 자리 표시자를 찾아 **TestPa55w.rd** 로 바꿉니다.

        > **참고**: 예를 들어, 연결 문자열이 원래 ``Server=tcp:polysqlsrvrinstructor.database.windows.net,1433;Initial Catalog=AdventureWorks;User ID={your_username};Password={your_password};``인 경우, 업데이트된 연결 문자열은 ``Server=tcp:polysqlsrvrinstructor.database.windows.net,1433;Initial Catalog=AdventureWorks;User ID=testuser;Password=TestPa55w.rd;``이 됩니다.

1.  블레이드에서 **쿼리 편집기(미리 보기)** 링크를 찾아 선택합니다.

1.  쿼리 편집기 창에서 다음 작업을 수행합니다.

    1.  **로그인** 텍스트 상자에 **testuser** 를 입력합니다.

    1.  **암호** 텍스트 상자에 **TestPa55w.rd** 를 입력합니다.

    1.  **확인** 을 선택합니다.

1.  열린 쿼리 편집기에서 다음 쿼리를 입력합니다.

```
    SELECT * FROM AdventureWorks.dbo.Models
```

1.  **실행** 을 선택하여 쿼리를 실행한 다음 결과를 살펴봅니다.

    > **참고**: 이 쿼리는 웹 애플리케이션의 홈페이지에서 모델 목록을 반환합니다.

1.  쿼리 편집기에서 기존 쿼리를 다음 쿼리로 바꿉니다.

```
    SELECT * FROM AdventureWorks.dbo.Products
```

1.  **실행** 을 선택하여 쿼리를 실행한 다음 결과를 살펴봅니다.

    > **참고**: 이 쿼리는 각 모델과 연결된 제품 목록을 반환합니다.

#### 검토

이 연습에서는 웹 애플리케이션에 사용할 모든 리소스를 가져왔습니다.

### 연습 3: .NET 웹 애플리케이션 열기 및 구성

#### 작업 1: 웹 애플리케이션 열기 및 빌드

1.  **시작** 화면에서 **Visual Studio Code** 타일을 선택합니다.

1.  **파일** 메뉴에서 **폴더 열기** 를 선택합니다.

1.  열리는 **파일 탐색기** 창에서 **Allfiles (F):\\Allfiles\\Labs\\04\\Starter\\AdventureWorks** 를 찾은 다음 **폴더 선택** 을 선택합니다.

1.  **Visual Studio Code** 창에서 탐색기 창의 바로 가기 메뉴를 마우스 오른쪽 단추로 클릭하거나 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 눌러 .NET 웹 애플리케이션을 빌드합니다.

```
    dotnet build
```

    > **참고**: **dotnet build** 명령은 폴더의 모든 프로젝트를 빌드하기 전에 누락된 NuGet 패키지를 자동으로 복원합니다.

1.  터미널에 출력된 빌드의 결과를 확인합니다. 오류나 경고 메시지 없이 빌드가 성공적으로 완료되어야 합니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 2: SQL 연결 문자열 업데이트

1.  **Visual Studio Code** 창의 탐색기 창에서 **AdventureWorks.Web** 프로젝트를 확장합니다.

1.  **appsettings.json** 파일을 엽니다.

1.  3행의 JSON(JavaScript Object Notation) 개체에서 **ConnectionStrings.AdventureWorksSqlContext** 경로를 찾습니다. 현재 값이 비어 있는지 확인합니다.

```
    "ConnectionStrings": {
        "AdventureWorksSqlContext": "",
        ...
    },
```

1.  이전에 랩에서 기록한 SQL 데이터베이스의 **ADO.NET(SQL 인증) 연결 문자열** 에 값을 설정하여 **AdventureWorksSqlContext** 속성의 값을 업데이트합니다.

    > **참고**: 여기에서는 업데이트된 연결 문자열을 사용하는 것이 중요합니다. 포털에서 복사한 원본 연결 문자열에는 SQL 데이터베이스에 연결하는 데 필요한 사용자 이름과 암호가 없습니다.

1.  **appsettings.json** 파일을 저장합니다.

#### 작업 3: Blob 기본 URL 업데이트

1.  8줄의 JSON 개체에서 **Settings.BlobContainerUrl** 경로를 찾습니다. 현재 값이 비어 있는지 확인합니다.

```
    "Settings": {
        "BlobContainerUrl": "",
        ...
    }
```

1.  값을 이전에 랩에서 기록한 **images** 라는 Azure Storage Blob 컨테이너의 **URL** 속성으로 설정하여 **BlobContainerUrl** 속성의 값을 업데이트합니다.

1.  **appsettings.json** 파일을 저장합니다.

#### 작업 4: 웹 애플리케이션 유효성 검사

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 터미널 컨텍스트를 **AdventureWorks.Web** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Web\
```

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 .NET Core 웹 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: **dotnet run** 명령은 프로젝트의 모든 변경 내용을 자동으로 빌드한 다음 디버거를 연결하지 않고 웹 애플리케이션을 시작합니다. 이 명령은 실행 중인 애플리케이션의 URL과 할당된 포트를 출력합니다.

1.  작업 표시줄에서 **Microsoft Edge** 아이콘을 선택합니다.

1.  열린 브라우저 창에서 현재 실행 중인 웹 애플리케이션(<http://localhost:5000>)으로 이동합니다.

1.  웹 애플리케이션에서 첫 페이지에 표시된 모델 목록을 살펴봅니다.

1.  **Water Bottle** 모델을 찾아 **View Details** 를 선택합니다.

1.  **Water Bottle** 제품 세부 정보 페이지에서 **Add to Cart** 를 찾은 다음 체크 아웃 기능이 현재 **비활성화**되어 있는지 확인합니다.

1.  웹 애플리케이션을 표시한 브라우저 창을 닫습니다.

1.  **Visual Studio Code** 창으로 돌아가서 **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련 프로세스를 닫습니다.

#### 검토

이 연습에서는 Azure의 리소스에 연결하도록 ASP.NET 웹 애플리케이션을 구성했습니다.

### 연습 4: SQL 데이터를 Azure Cosmos DB로 마이그레이션

#### 작업 1: 마이그레이션 프로젝트 만들기

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 동일한 이름의 폴더에 **AdventureWorks.Migrate** 라는 새 .NET 프로젝트를 만듭니다.

```
    dotnet new console --name AdventureWorks.Migrate
```

    > **참고**: **dotnet new** 명령은 새 **콘솔** 프로젝트를 프로젝트와 이름이 같은 폴더에 만듭니다.

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 기존 **AdventureWorks.Models** 프로젝트에 참조를 추가합니다.

```
    dotnet add .\AdventureWorks.Migrate\AdventureWorks.Migrate.csproj reference .\AdventureWorks.Models\AdventureWorks.Models.csproj
```

    > **참고**: **dotnet add reference** 명령은 **AdventureWorks.Model** 프로젝트에 포함된 모델 클래스 참조를 추가합니다.

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 기존 **AdventureWorks.Context** 프로젝트에 참조를 추가합니다.

```
    dotnet add .\AdventureWorks.Migrate\AdventureWorks.Migrate.csproj reference .\AdventureWorks.Context\AdventureWorks.Context.csproj
```

    > **참고**: **dotnet add reference** 명령은 **AdventureWorks.Context** 프로젝트에 포함된 컨텍스트 클래스 참조를 추가합니다.

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 터미널 컨텍스트를 **AdventureWorks.Migrate** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Migrate\
```

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 NuGet에서 **Microsoft.EntityFrameworkCore.SqlServer** 버전 2.2.6을 가져옵니다.

```
    dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 3.0.1
```

    > **참고**: **dotnet add package** 명령은 **NuGet** 에서 **Microsoft.EntityFrameworkCore.SqlServer** 패키지를 추가합니다. 자세한 내용은 다음을 참조하십시오. [Microsoft.EntityFrameworkCore.SqlServer](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.SqlServer/3.0.1).

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 NuGet에서 **Microsoft.Azure.Cosmos** 의 버전 3.4.1을 가져옵니다.

```
    dotnet add package Microsoft.Azure.Cosmos --version 3.4.1
```

    > **참고**: **dotnet add package** 명령은 **NuGet** 에서 **Microsoft.Azure.Cosmos** 패키지를 추가합니다. 자세한 내용은 다음을 참조하십시오. [Microsoft.Azure.Cosmos](https://www.nuget.org/packages/Microsoft.Azure.Cosmos/3.4.1).

1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 애플리케이션을 빌드합니다.

```
    dotnet build
```

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 2: .NET 클래스 만들기 

1.  **Visual Studio Code** 창의 탐색기 창에서 **AdventureWorks.Migrate** 프로젝트를 펼칩니다.

1.  **Program.cs** 파일을 엽니다.

1.  **Program.cs** 파일의 코드 편집기 탭에서 기존 파일의 모든 코드를 삭제합니다.

1.  다음 코드 줄을 추가하여 참조된 **AdventureWorks.Models** 및 **AdventureWorks.Context** 프로젝트의 **AdventureWorks.Models** 및 **AdventureWorks.Context** 네임스페이스를 가져옵니다.

```
    using AdventureWorks.Context;
    using AdventureWorks.Models;
```

1.  다음 코드 줄을 추가하여 NuGet에서 가져온 **Microsoft.Azure.Cosmos** 패키지에서 **Microsoft.Azure.Cosmos** 네임스페이스를 가져옵니다.

```
    using Microsoft.Azure.Cosmos;
```

1.  다음 코드 줄을 추가하여 NuGet에서 가져온 **Microsoft.EntityFrameworkCore.SqlServer** 패키지에서 **Microsoft.EntityFrameworkCore** 네임스페이스를 가져옵니다.

```
    using Microsoft.EntityFrameworkCore;
```

1.  다음 코드 줄을 추가하여 이 파일에 사용할 기본 제공 네임스페이스에 대해 **using** 지시문을 추가합니다.

```
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Threading.Tasks;
```

1.  다음 코드를 입력하여 새 **Program** 클래스를 만듭니다.

```
    public class Program
    {
    }
```

1.  **Program** 클래스 내에서 다음 코드 줄을 입력하여 **sqlDBConnectionString** 이라는 새 문자열 상수를 만듭니다.

```
    private const string sqlDBConnectionString = "";
```

1.  이 랩의 앞 부분에서 기록한 SQL 데이터베이스의 **ADO.NET(SQL 인증) 연결 문자열** 에 해당 값을 설정하여 **sqlDBConnectionString** 문자열 상수를 업데이트합니다.

    > **참고**: 여기에서는 업데이트된 연결 문자열을 사용하는 것이 중요합니다. 포털에서 복사한 원본 연결 문자열에는 SQL 데이터베이스에 연결하는 데 필요한 사용자 이름과 암호가 없습니다.

1.  **Program** 클래스 내에서 다음 코드 줄을 입력하여 **cosmosDBConnectionString** 이라는 새 문자열 상수를 만듭니다. 

```
    private const string cosmosDBConnectionString = "";
```

1.  이 랩의 앞 부분에서 기록한 Azure Cosmos DB 계정의 **기본 연결 문자열** 로 값을 설정하여 **cosmosDBConnectionString** 문자열 상수를 업데이트합니다.

1.  **Program** 클래스 내에서 다음 코드 줄을 입력하여 새 비동기 **Main** 메서드를 만듭니다.

```
    public static async Task Main(string[] args)
    {
    }
```

1.  **기본** 메서드 내에서 다음 코드 줄을 추가하여 콘솔에 소개 메시지를 출력합니다.

```
    await Console.Out.WriteLineAsync("Start Migration");
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 터미널 컨텍스트를 **AdventureWorks.Migrate** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Migrate\
```

1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 애플리케이션을 빌드합니다.

```
    dotnet build
```

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 3: Entity Framework를 사용하여 SQL 데이터베이스 레코드 가져오기

1.  **Program.cs** 파일 내 **Program** 클래스의 **Main** 메서드 내에서 다음 코드 줄을 추가하여 *sqlDBConnectionString* 변수를 연결 문자열 값으로 전달하면서 **AdventureWorksSqlContext** 클래스의 새 인스턴스를 만듭니다.

```
    using AdventureWorksSqlContext context = new AdventureWorksSqlContext(sqlDBConnectionString);
```

1.  **Main** 메서드 내에서 다음 코드 블록을 추가하여 LINQ(언어 통합 쿼리)를 발행함으로써 데이터베이스에서 모든 **Models** 및 하위 **Products** 를 가져오고 메모리 내 **List<>** 컬렉션에 저장합니다.

```
    List<Model> items = await context.Models
        .Include(m => m.Products)
        .ToListAsync<Model>();
```

1.  **기본** 메서드 내에서 다음 코드 줄을 추가하여 SQL Database에서 가져온 레코드 수를 출력합니다.

```
    await Console.Out.WriteLineAsync($"Total Azure SQL DB Records: {items.Count}");
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 터미널 컨텍스트를 **AdventureWorks.Migrate** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Migrate\
```
    
1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 .NET Core 애플리케이션을 빌드합니다.

```
    dotnet build
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\04\\Solution\\AdventureWorks\\AdventureWorks.Migrate** 폴더에 있는 **Program.cs** 파일을 검토합니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 4: Azure Cosmos DB에 항목을 삽입합니다.

1.  **Program.cs** 파일 내 **Program** 클래스의 **Main** 메서드 내에서 다음 코드 줄을 추가하여 *cosmosDBConnectionString* 변수를 연결 문자열 값으로 전달하면서 **CosmosClient** 클래스의 새 인스턴스를 만듭니다.

```
    using CosmosClient client = new CosmosClient(cosmosDBConnectionString);
```

1.  **Main** 메서드 내에서 다음 코드 줄을 추가하여 Azure Cosmos DB 계정에 아직 없는 경우 새 **Database** 인 **Retail** 을 만듭니다.

```
    Database database = await client.CreateDatabaseIfNotExistsAsync("Retail");
```

1.  **Main** 메서드 내에서 다음 코드 블록을 추가하여 파티션 키 경로가 **/Category** 이고 처리량이 **1000** 요청 단위인 **Online** 이라는 새 **컨테이너**(Azure Cosmos DB 계정에 아직 없는 경우)를 만듭니다.

```
    Container container = await database.CreateContainerIfNotExistsAsync("Online",
        partitionKeyPath: $"/{nameof(Model.Category)}",
        throughput: 1000
    );
```

1.  **Main** 메서드 내에서 다음 코드 줄을 추가하여 *count* 라는 **int** 변수를 만듭니다.

```
    int count = 0;
```

1.  **Main** 메서드 내에서 다음 코드 블록을 추가하여 **items** 컬렉션의 개체를 반복하는 **foreach** 반복을 만듭니다.

```
    foreach (var item in items)
    {
    }
```

1.  **Main** 메서드의 **foreach** 반복 내에서 다음 코드 줄을 추가하여 개체를 Azure Cosmos DB 컬렉션에 **upsert** 하고 결과를 **document** 라는 *ItemResponse<>* 형식의 변수에 결과를 저장합니다.

```
    ItemResponse<Model> document = await container.UpsertItemAsync<Model>(item);
```

1.  **Main** 메서드에 포함된 **foreach** 반복 내에서 다음 코드 줄을 추가하여 각 upsert 작업의 활동 ID를 인쇄합니다.

```
    await Console.Out.WriteLineAsync($"Upserted document #{++count:000} [Activity Id: {document.ActivityId}]");
```

1.  다시 **Main** 메서드 내에서(**foreach** 루프 외부) 다음 코드 줄을 추가하여 Azure Cosmos DB로 내보낸 문서 수를 인쇄합니다.

```
    await Console.Out.WriteLineAsync($"Total Azure Cosmos DB Documents: {count}");
```

1.  **Program.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 터미널 컨텍스트를 **AdventureWorks.Migrate** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Migrate\
```
    
1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 애플리케이션을 빌드합니다.

```
    dotnet build
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\04\\Solution\\AdventureWorks\\AdventureWorks.Migrate** 폴더에 있는 **Program.cs** 파일을 검토합니다.

#### 작업 5: 마이그레이션

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: **dotnet run** 명령은 콘솔 애플리케이션을 시작합니다.

1.  초기 SQL 레코드 수, 개별 upsert 활동 식별자, 최종 Azure Cosmos DB 문서 수를 비롯하여 화면에 출력되는 다양한 데이터를 확인합니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 6: 마이그레이션 유효성 검사

1.  Azure Portal이 있는 **Microsoft Edge** 브라우저 창으로 돌아갑니다.

1.  Azure Portal의 탐색 창에서 **리소스 그룹** 링크를 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩의 앞부분에서 만든 **PolyglotData** 리소스 그룹을 찾아 선택합니다.

1.  **PolyglotData** 블레이드에서 이 랩의 앞부분에서 만든 **polycosmos*[yourname]*** Azure Cosmos DB 계정을 선택합니다.

1.  **Azure Cosmos DB 계정** 블레이드에서 **데이터 탐색기** 링크를 찾아 선택합니다.

1.  데이터 탐색기 창에서 **Retail** 데이터베이스 노드를 펼칩니다.

1.  **Online** 컨테이너 노드 오른쪽 햄버거메뉴에서 **New SQL Query** 를 선택합니다.

    > **참고**: 이 옵션의 레이블은 숨겨져 있을 수 있습니다. 데이터 탐색기 창의 아이콘 위로 마우스를 가져가면 레이블을 볼 수 있습니다.

1.  쿼리 탭에서 다음 텍스트를 입력합니다.

```
    SELECT * FROM models
```

1.  **쿼리 실행** 을 선택한 다음 쿼리가 반환하는 JSON 모델 목록을 살펴봅니다.

1.  쿼리 편집기로 돌아가서 기존 텍스트를 다음 텍스트로 바꿉니다.

```
    SELECT VALUE COUNT(1) FROM models
```

1.  **쿼리 실행** 을 선택한 다음 **COUNT** 집계 작업의 결과를 살펴봅니다.

1.  **Visual Studio Code** 창으로 돌아갑니다.

#### 복습

이 연습에서는 Entity Framework 및 Azure Cosmos DB용 .NET SDK를 사용하여 SQL Database에서 Azure Cosmos DB로 데이터를 마이그레이션했습니다.

### 연습 5: .NET을 사용한 Azure Cosmos DB 액세스

#### 작업 1: Cosmos SDK 및 참조를 사용하여 라이브러리 업데이트

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 터미널 컨텍스트를 **AdventureWorks.Context** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Context\
```

1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 NuGet에서 **Microsoft.Azure.Cosmos** 를 가져옵니다.

```
    dotnet add package Microsoft.Azure.Cosmos --version 3.4.1
```

    > **참고**: **dotnet add package** 명령은 **NuGet** 에서 **Microsoft.Azure.Cosmos** 패키지를 추가합니다. 자세한 내용은 다음을 참조하십시오. [Microsoft.Azure.Cosmos](https://www.nuget.org/packages/Microsoft.Azure.Cosmos/3.4.1).

1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 빌드합니다.

```
    dotnet build
```

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 2: Azure Cosmos DB에 연결하는 .NET 코드 작성

1.  **Visual Studio Code** 창의 탐색기 창에서 **AdventureWorks.Context** 프로젝트를 펼칩니다.

1.  바로 가기 메뉴에 액세스하거나 **AdventureWorks.Context** 폴더 노드를 마우스 오른쪽 단추로 클릭하거나 활성화한 다음 **새 파일** 을 선택합니다.

1.  새 파일 프롬프트에서 **AdventureWorksCosmosContext.cs** 를 입력합니다.

1.  **AdventureWorksCosmosContext.cs** 파일의 코드 편집기 탭에서 다음 코드 줄을 추가하여 참조된 **AdventureWorks.Models** 프로젝트에서 **AdventureWorks.Models** 네임스페이스를 가져옵니다.

```
    using AdventureWorks.Models;
```

1.  다음 코드 줄을 추가하여 NuGet에서 가져온 **Microsoft.Azure.Cosmos** 패키지에서 **Microsoft.Azure.Cosmos** 및 **Microsoft.Azure.Cosmos.Linq** 네임스페이스를 가져옵니다.

```
    using Microsoft.Azure.Cosmos;
    using Microsoft.Azure.Cosmos.Linq;
```

1.  다음 코드 줄을 추가하여 이 파일에 사용할 기본 제공 네임스페이스에 대해 **using** 지시문을 추가합니다.

```
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Threading.Tasks;
```

1.  다음 코드를 입력하여 **AdventureWorks.Context** 네임스페이스 블록을 추가합니다.

```
    namespace AdventureWorks.Context
    {
    }
```

1.  **AdventureWorks.Context** 네임스페이스 내에서 다음 코드를 입력하여 새 **AdventureWorksCosmosContext** 클래스를 만듭니다.

```
    public class AdventureWorksCosmosContext
    {
    }
```

1.  이 클래스가 **IAdventureWorksProductContext** 인터페이스를 구현한다는 것을 나타내는 사양을 추가하여 **AdventureWorksCosmosContext** 클래스 선언을 업데이트합니다.

```
    public class AdventureWorksCosmosContext : IAdventureWorksProductContext
    {
    }
```

1.  **AdventureWorksCosmosContext** 클래스 내에서 다음 코드 줄을 입력하여 **_container** 라는 새 읽기 전용 *Container* 변수를 만듭니다.

```
    private readonly Container _container;
```

1.  **AdventureWorksCosmosContext** 클래스 내에서 다음 서명을 사용하여 새 생성자를 추가합니다.

```
    public AdventureWorksCosmosContext(string connectionString, string database = "Retail", string container = "Online")
    {
    }
```

1.  생성자 내에서 다음 코드 블록을 추가하여 **CosmosClient** 클래스의 새 인스턴스를 만든 다음 클라이언트에서 **Database** 및 **Container** 인스턴스를 모두 가져옵니다.

```
    _container = new CosmosClient(connectionString)
        .GetDatabase(database)
        .GetContainer(container);
```

1.  **AdventureWorksCosmosContext** 클래스 내에서 다음 서명을 사용하여 새 **FindModelAsync** 메서드를 추가합니다.

```
    public async Task<Model> FindModelAsync(Guid id)
    {
    }
```

1.  **FindModelAsync** 메서드 내에서 다음 코드 블록을 추가하여 LINQ 쿼리를 만들고, 이를 반복기로 변환하고, 결과 집합을 반복한 다음, 결과 집합에서 단일 항목을 반환합니다.

```
    var iterator = _container.GetItemLinqQueryable<Model>()
        .Where(m => m.id == id)
        .ToFeedIterator<Model>();

    List<Model> matches = new List<Model>();
    while (iterator.HasMoreResults)
    {
        var next = await iterator.ReadNextAsync();
        matches.AddRange(next);
    }

    return matches.SingleOrDefault();
```

1.  **AdventureWorksCosmosContext** 클래스 내에서 다음 서명을 사용하여 새 **GetModelsAsync** 메서드를 추가합니다.

```
    public async Task<List<Model>> GetModelsAsync()
    {
    }
```

1.  **GetModelsAsync** 메서드 내에서 다음 코드 블록을 추가하여 SQL 쿼리를 실행하고, 쿼리 결과 반복기를 가져오고, 결과 집합을 반복한 다음, 모든 결과의 집합을 반환합니다.

```
    string query = $@"SELECT * FROM items";

    var iterator = _container.GetItemQueryIterator<Model>(query);

    List<Model> matches = new List<Model>();
    while (iterator.HasMoreResults)
    {
        var next = await iterator.ReadNextAsync();
        matches.AddRange(next);
    }

    return matches;
```

1.  **AdventureWorksCosmosContext** 클래스 내에서 다음 서명을 사용하여 새 **FindProductAsync** 메서드를 추가합니다.

```
    public async Task<Product> FindProductAsync(Guid id)
    {
    }
```

1.  **FindProductAsync** 메서드 내에서 다음 코드 블록을 추가하여 SQL 쿼리를 실행하고, 쿼리 결과 반복기를 가져오고, 결과 집합을 반복한 다음, 결과 집합에서 단일 항목을 반환합니다.

```
    string query = $@"SELECT VALUE products
                        FROM models
                        JOIN products in models.Products
                        WHERE products.id = '{id}'";

    var iterator = _container.GetItemQueryIterator<Product>(query);

    List<Product> matches = new List<Product>();
    while (iterator.HasMoreResults)
    {
        var next = await iterator.ReadNextAsync();
        matches.AddRange(next);
    }

    return matches.SingleOrDefault();
```

1.  **AdventureWorksCosmosContext.cs** 파일을 저장합니다.

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 터미널 컨텍스트를 **AdventureWorks.Context** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Context\
```
    
1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 .NET 웹 애플리케이션을 빌드합니다.

```
    dotnet build
```

    > **참고**: 빌드 오류가 있는 경우 **Allfiles (F):\\Allfiles\\Labs\\04\\Solution\\AdventureWorks\\AdventureWorks.Context** 폴더에 있는 **AdventureWorksCosmosContext.cs** 파일을 검토합니다.

1.  **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련된 모든 작업을 종료합니다.

#### 작업 3: Azure Cosmos DB 연결 문자열 업데이트

1.  **Visual Studio Code** 창의 탐색기 창에서 **AdventureWorks.Web** 프로젝트를 확장합니다.

1.  **appsettings.json** 파일을 엽니다.

1.  4줄의 JSON 개체에서 **ConnectionStrings.AdventureWorksCosmosContext** 경로를 찾습니다. 현재 값이 비어 있는지 확인합니다.

```
    "ConnectionStrings": {
        ...
        "AdventureWorksCosmosContext": "",
        ...
    },
```

1.  이 랩의 앞부분에서 기록한 Azure Cosmos DB 계정의 **기본 연결 문자열** 로 값을 설정하여 **AdventureWorksCosmosContext** 속성 값을 업데이트합니다.

1.  **appsettings.json** 파일을 저장합니다.

#### 작업 4: .NET 애플리케이션 시작 논리 업데이트

1.  **Visual Studio Code** 창의 탐색기 창에서 **AdventureWorks.Web** 프로젝트를 확장합니다.

1.  **Startup.cs** 파일을 엽니다.

1.  **시작** 클래스에서 기존 **ConfigureProductService** 메서드를 찾습니다.

```
    public void ConfigureProductService(IServiceCollection services)
    {
        services.AddScoped<IAdventureWorksProductContext, AdventureWorksSqlContext>(provider =>
            new AdventureWorksSqlContext(
                _configuration.GetConnectionString(nameof(AdventureWorksSqlContext))
            )
        );
    }
```

    > **참고**: 현재 제품 서비스는 SQL을 데이터베이스로 사용합니다.

1.  **ConfigureProductService** 메서드 내에서 기존 코드 줄을 모두 삭제합니다.

```
    public void ConfigureProductService(IServiceCollection services)
    {
    }
```

1.  **ConfigureProductService** 메서드 내에서 다음 코드 블록을 추가하여 이 랩의 앞 부분에서 만든 **AdventureWorksCosmosContext** 구현으로 제품 공급자를 변경합니다.

```
    services.AddScoped<IAdventureWorksProductContext, AdventureWorksCosmosContext>(provider =>
        new AdventureWorksCosmosContext(
            _configuration.GetConnectionString(nameof(AdventureWorksCosmosContext))
        )
    );
```

1.  **Startup.cs** 파일을 저장합니다.

#### 작업 5: .NET 애플리케이션이 Azure Cosmos DB에 성공적으로 연결되었는지 확인

1.  **Visual Studio Code** 창에서 바로 가기 메뉴에 액세스하거나 탐색기 창을 마우스 오른쪽 단추로 클릭 또는 활성화한 다음 **터미널에서 열기** 를 선택합니다.

1.  열린 명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 터미널 컨텍스트를 **AdventureWorks.Web** 폴더로 전환합니다.

```
    cd .\AdventureWorks.Web\
```

1.  명령 프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 .NET Core 웹 애플리케이션을 실행합니다.

```
    dotnet run
```

    > **참고**: **dotnet run** 명령은 프로젝트의 모든 변경 내용을 자동으로 빌드한 다음 디버거를 연결하지 않고 웹 애플리케이션을 시작합니다. 이 명령은 실행 중인 애플리케이션의 URL과 할당된 포트를 출력합니다.

1.  작업 표시줄에서 **Microsoft Edge** 아이콘을 선택합니다.

1.  열린 브라우저 창에서 현재 실행 중인 웹 애플리케이션(<http://localhost:5000>)으로 이동합니다.

1.  웹 애플리케이션에서 첫 페이지에 표시된 모델 목록을 살펴봅니다.

1.  **Touring-1000** 모델을 찾아 **View Details** 를 선택합니다.

1.  **Touring-1000** 제품 세부 정보 페이지에서 다음 작업을 수행합니다.

    1.  **Select Options** 목록에서 **Touring-1000 Yellow, 50, $2,384.07** 을 선택합니다.
    
    1.   **장바구니에 추가** 기능이 여전히 비활성화되어 있는지 확인합니다.

1.  웹 애플리케이션을 표시한 브라우저 창을 닫습니다.

1.  **Visual Studio Code** 창으로 돌아가서 **터미널 종료** 또는 **휴지통** 아이콘을 선택하여 현재 열려 있는 터미널 및 관련 프로세스를 닫습니다.

#### 검토

이 연습에서는 .NET SDK를 사용하여 Azure Cosmos DB 컬렉션을 쿼리하는 C# 코드를 작성했습니다.

### 연습 6: 구독 정리 

#### 작업 1: Azure Cloud Shell 열기

1.  포털에서 **Cloud Shell** 아이콘을 선택하여 새 셸 인스턴스를 엽니다.

    > **참고**: **Cloud Shell** 아이콘은 초과(\>) 기호와 밑줄 문자(\_)로 표시됩니다.

1.  구독을 사용하여 Cloud Shell을 처음으로 여는 경우, 처음 사용할 경우에만 **Azure Cloud Shell 시작 마법사** 를 사용하여 Cloud Shell를 구성할 수 있습니다. 마법사에서 다음 작업을 수행합니다.
    
    1.  대화 박스는 셸을 사용하여 시작할 새 스토리지 계정을 만들라는 메시지를 표시합니다. 기본 설정을 수락하고 **스토리지 만들기** 를 선택합니다.
    
    > **참고**: 랩을 진행하기 전에 Cloud Shell이 초기 설치 절차를 완료할 때까지 기다립니다. Cloud Shell 구성 옵션이 표시되지 않는 경우 이 과정의 랩에서 기존 구독을 사용하고 있기 때문일 수 있습니다. 랩은 새 구독을 사용한다는 가정 하에서 작성됩니다.

1.  포털의 **Cloud Shell** 명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 구독의 모든 리소스 그룹을 나열합니다.

```
    az group list
```

1.  프롬프트에서 다음 명령을 입력하고 Enter 키를 선택하여 리소스 그룹을 삭제하는 가능한 명령 목록을 가져옵니다.

```
    az group delete --help
```

#### 작업 2: 리소스 그룹 삭제

1.  명령 프롬프트에서 다음 명령을 입력하고 엔터를 선택하여 **PolyglotData** 리소스 그룹을 삭제합니다.

```
    az group delete --name PolyglotData --no-wait --yes
```
    
1.  포털에서 Cloud Shell 창을 닫습니다.

#### 작업 3: 활성 애플리케이션 닫기

1.  현재 실행 중인 Microsoft Edge 애플리케이션을 닫습니다.

1.  현재 실행 중인 Visual Studio Code 애플리케이션을 닫습니다.

#### 복습

이 연습에서는 이 랩에 사용된 리소스 그룹을 제거하여 구독을 정리했습니다.
