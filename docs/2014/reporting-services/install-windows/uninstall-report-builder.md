---
title: 卸載單機版的報表產生器（報表產生器） |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: eeb260942f378eb1e93751fc118f82e67a13d45b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108654"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a>解除安裝單機版報表產生器 (報表產生器)
  您可以從控制台或命令列解除安裝單機版本的報表產生器。 如果沒有解除安裝 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]，您就不能解除安裝 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 版本的報表產生器。  
  
 從命令列解除安裝報表產生器所用的語法與用來安裝報表產生器的語法完全相同，不過您會使用 /x 選項來取代 /i 選項。 解除安裝的命令列也可以包含 /quiet 選項和其他標準選項。 如果已經移除了報表產生器的 Windows Installer 套件 (ReportBuilder3_x86.msi)，您就無法輕鬆地使用命令列來解除安裝報表產生器。 若要深入了解有關如何使用 GUID 來移除報表產生器的詳細資訊，請參閱 MSDN Library 上 msiexec 程式的文件集。  
  
 如果報表產生器使用的資料夾包含自訂檔案，移除報表產生器時便會保留這些資料夾和檔案。 系統只會移除報表產生器的檔案。  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a>若要從控制台解除安裝報表產生器  
  
1.  在 **[開始]** 功能表上，按一下 **[控制台]** 。  
  
2.  在 [控制台] 中，按一下 **[程式和功能]** 。  
  
3.  在 [名稱][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 清單中找出 **** 報表產生器，然後按一下它。  
  
4.  按一下 **[解除安裝]** 。  
  
5.  如果出現確認解除安裝報表產生器的提示，請按一下 **[是]** 。  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>若要從命令列解除安裝報表產生器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]** 。  
  
2.  在 [**開啟**] 文字方塊中，輸入`cmd.`  
  
3.  在 [命令提示字元] 視窗中，導覽至包含 ReportBuilder3_x86.msi 的資料夾。  
  
4.  輸入如下的基本命令列：  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 如果可以包含記錄功能，請使用如下所示的命令列：  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  按 **Enter** 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md)   
 [安裝獨立版本的報表產生器 &#40;報表產生器&#41;](install-report-builder.md)  
  
  
