---
title: Развертывание пользовательской сборки | Документы Майкрософт
description: Узнайте, как развернуть пользовательскую сборку в службах Reporting Microsoft SQL Server Reporting Services. Также узнайте, как предоставлять привилегии пользовательским сборкам, помимо разрешений на выполнение.
ms.date: 11/23/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.topic: reference
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2c68562c1be1817d8f7457f680b4f45169de4a1f
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96166887"
---
# <a name="deploying-a-custom-assembly"></a>Развертывание пользовательской сборки
  Чтобы развернуть пользовательскую сборку в службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], поместите сборку в папки приложения и конструктора отчетов, и сервера отчетов. По умолчанию пользовательским сборкам в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предоставляется разрешение **Выполнение**. Чтобы предоставить пользовательским сборкам права доступа, кроме разрешения на выполнение, необходимо изменить файл конфигурации rssrvpolicy.config для сервера отчетов и файл конфигурации rspreviewpolicy.config для окна предварительного просмотра конструктора отчетов. Также можно установить пользовательскую сборку в глобальный кэш сборок.  
  
> [!NOTE]  
>  Для конструктора отчетов предусмотрено два режима предварительного просмотра: вкладка предварительного просмотра и всплывающее окно предварительного просмотра, которое вызывается при запуске проекта отчета в режиме **DebugLocal**. На вкладке предварительного просмотра все выражения отчета выполняются с помощью набора разрешений **FullTrust** и не применяются параметры политики безопасности. Всплывающее окно предварительного просмотра предназначено для имитации функциональных возможностей сервера отчетов и поэтому имеет файл конфигурации политики, который необходимо изменить (возможно, при участии администратора), чтобы использовать пользовательские сборки в конструкторе отчетов. Это всплывающее окно предварительного просмотра также блокирует пользовательскую сборку. Поэтому для изменения или обновления кода пользовательской сборки необходимо закрыть окно предварительного просмотра.  
  
## <a name="to-deploy-a-custom-assembly-in-reporting-services"></a>Развертывание пользовательской сборки в службах Reporting Services  
  
1.  Скопируйте пользовательскую сборку из каталога построения в папку bin на сервере отчетов или в папку конструктора отчетов. 

     Размещение пользовательской сборки в папке bin на сервере отчетов позволяет публиковать отчеты, которые ссылаются на эту пользовательскую сборку. Расположение папки bin по умолчанию для сервера отчетов:

     Reporting Services 2016
     ```
     %ProgramFiles%\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer\bin
     ```
     Reporting Services 2017 или более поздней версии
     ```
     %ProgramFiles%\Microsoft SQL Server Reporting Services\SSRS\ReportServer\bin
     ```
     Если разместить ее в папке конструктора отчетов, вы сможете запускать отчеты, которые ссылаются на такую пользовательскую сборку, в конструкторе отчетов, а также выполнять отладку таких отчетов. Расположение конструктора отчетов по умолчанию:

     Visual Studio 2012
     ```
     C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\PrivateAssemblies
     ```
     Visual Studio 2013
     ```
     C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE\PrivateAssemblies
     ```
     Visual Studio 2015
     ```
     C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\PrivateAssemblies
     ```
     Visual Studio 2017
     ```
     C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS
     ```
     Visual Studio 2019
     ```
     C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS
     ```  
2.  Откройте соответствующий файл конфигурации. Расположение файла rssrvpolicy.config для сервера отчетов по умолчанию:

     Reporting Services 2016
     ```
     %ProgramFiles%\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer
     ```
     Reporting Services 2017 или более поздней версии
     ```
     %ProgramFiles%\Microsoft SQL Server Reporting Services\SSRS\ReportServer
     ```
     Файлы для обновления конструктора отчетов:

     Visual Studio 2012
     ```
     C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\PrivateAssemblies\PreviewProcessingService.exe.config
     C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\PrivateAssemblies\RSPreviewPolicy.config
     C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\PrivateAssemblies\RSReportDesigner.config
     C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE\PrivateAssemblies\RSReportHost11.exe.config
     ```
     Visual Studio 2013
     ```
     C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE\PrivateAssemblies\PreviewProcessingService.exe.config
     C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE\PrivateAssemblies\RSPreviewPolicy.config
     C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE\PrivateAssemblies\RSReportDesigner.config
     C:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE\PrivateAssemblies\RSReportHost.exe.config
     ```
     Visual Studio 2015
     ```
     C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\PrivateAssemblies\PreviewProcessingService.exe.config
     C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\PrivateAssemblies\RSPreviewPolicy.config
     C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\PrivateAssemblies\RSReportDesigner.config
     C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\PrivateAssemblies\RSReportHost.exe.config
     ```
     Visual Studio 2017
     ```
     C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\PreviewProcessingService.exe.config
     C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\RSPreviewPolicy.config
     C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\RSReportDesigner.config
     C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\RSReportHost.exe.config
     ```
     Visual Studio 2019
     ```
     C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\PreviewProcessingService.exe.config
     C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\RSPreviewPolicy.config
     C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\RSReportDesigner.config
     C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\SSRS\RSReportHost.exe.config
     ```    
3.  Добавьте группу кода для пользовательской сборки. Дополнительные сведения см. в разделе [Безопасная разработка (службы Reporting Services)](../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="updating-custom-assemblies"></a>Обновление пользовательских сборок  
 На некотором этапе может понадобиться обновить версию пользовательской сборки, на которую существуют ссылки в нескольких опубликованных отчетах. Если эта сборка уже существует в каталоге bin сервера отчетов или конструктора отчетов и номер версии сборки увеличивается или изменяется иным образом, уже опубликованные отчеты перестанут правильно работать. Будет необходимо обновить версию сборки, на которую ссылается элемент **CodeModules** определения отчета, и повторно опубликовать отчеты. Если известно, что пользовательская сборка будет часто обновляться, а отчетам, опубликованным в настоящий момент, необходимо ссылаться на новую сборку, рекомендуется использовать одинаковые номера версий для всех обновлений данной сборки.  
  
 Если не нужно ссылаться на новую версию сборки в опубликованных отчетах, можно развернуть пользовательскую сборку в глобальном кэше сборок. Глобальный кэш сборок может хранить несколько версий одной сборки, поэтому текущие отчеты могут ссылаться на предыдущую версию сборки, а вновь публикуемые отчеты — на обновленную сборку. Другим способом является задание перенаправления привязки сервера отчетов, чтобы вызвать принудительное перенаправление всех запросов старой сборки на новую сборку. Для этого необходимо изменить файлы сервера отчета Web.config и ReportingServicesService.exe.config. Запись файла конфигурации может иметь следующий вид:  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Работа со сборками и глобальным кэшем сборок](https://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
