---
title: 安裝 SQL Server Native Client |Microsoft Docs
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: MightyPen
ms.author: genemi
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 677450c306cdd85f3fec34b09ab8da9b45181844
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73788453"
---
# <a name="installing-sql-server-native-client"></a>安裝 SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 會在您安裝 [!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)] 時安裝。 
 
 沒有 SQL Server 2016 Native Client。 如需詳細資訊，請參閱[SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md)。 
 
您也可以從 SQL Server 2012 功能套件網頁取得 sqlncli.msi。 若要下載最新版本的 SQL Server Native Client，請移至[Microsoft® SQL Server® 2012 Feature Pack](https://www.microsoft.com/download/confirmation.aspx?id=29065)。 如果電腦上也安裝[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]了早于 SQL Server 2012 之前的 native client 版本， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client 11.0 將會與舊版並存安裝。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 檔案 (sqlncli11.dll、sqlnclir11.rll 和 s11ch_sqlncli.chm) 會安裝到下列位置：  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式的所有適當的登錄設定，都會在安裝程序時進行。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 標頭和程式庫檔 (sqlncli.h 和 sqlncli11.lib) 會安裝到下列位置：  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 除了在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝時進行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的安裝外，還可以利用名為 sqlncli.msi 的轉散發安裝程式，這個程式可以在下列位置的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝磁碟上找到：`%CD%\Setup\`。  
  
 您可以透過 sqlncli.msi 散佈 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。 當您部署應用程式時，可能必須安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。 使用 Chainer 和 Bootstrapper 技術是安裝多個封裝 (但對使用者卻好像是單一安裝) 的一種方法。 如需詳細資訊，請參閱[撰寫適用于 Visual Studio 2005 的自訂](https://go.microsoft.com/fwlink/?LinkId=115667)啟動載入器套件和[加入自訂的必要條件](https://go.microsoft.com/fwlink/?LinkId=115668)。  
  
 x64 和 Itanium 版本的 sqlncli.msi 會安裝 32 位元版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client。 如果應用程式的目標使用平台與當初開發時的平台不同，您可以從 Microsoft 下載中心下載 x64、Itanium 和 x86 版本的 sqlncli.msi。  
  
 當您叫用 sqlncli.msi 時，依預設會安裝用戶端元件。 用戶端元件是支援執行使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client 開發之應用程式的檔案。 如果也要安裝 SDK 元件，請在命令列上指定 `ADDLOCAL=All`。 例如：  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>無訊息安裝  
 如果您搭配 msiexec 使用 /passive、/qn、/qb 或 /qr 選項，則也必須指定 IACCEPTSQLNCLILICENSETERMS=YES，以明確指出您接受使用者授權條款。 此選項必須以全部大寫的字母指定。  
  
## <a name="uninstalling-sql-server-native-client"></a>解除安裝 SQL Server Native Client  
 因為[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]伺服器和工具之類的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]應用程式相依于[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client，所以在卸載所有相依的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]應用程式之前，請務必不要卸載 native client。 若要提供應用程式相依于[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的警告給使用者，請使用 MSI 中的 APPGUID 安裝選項，如下所示：  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 傳遞給 APPGUID 的值是您特定的產品代碼。 使用 Microsoft Installer 來封裝應用程式安裝程式時，必須建立產品代碼。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SQL Server Native Client 建立應用程式](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [安裝的使用說明主題](https://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
