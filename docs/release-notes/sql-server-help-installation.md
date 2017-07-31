---
title: "Окно справки и автономное содержимое для SQL Server | Документы Майкрософт"
ms.custom: 
ms.date: 06/27/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
ms.translationtype: HT
ms.sourcegitcommit: aad94f116c1a8b668c9a218b32372424897a8b4a
ms.openlocfilehash: ca52d53cf25fa0ead6abd9b870f4d8dab424d11a
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="help-viewer-and-offline-content-for-sql-server"></a>Окно справки и автономное содержимое для SQL Server
  
  
  
Эта статья описывает, как установить окно справки и просматривать документацию по SQL Server в автономном режиме. Здесь рассматривается документация для [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)], SQL Server 2016 и SQL Server 2017. 

## <a name="install-help-viewer"></a>Установка окна справки
Ниже перечислены средства, устанавливающие окно справки, с учетом используемой версии SQL Server. Установите одно из указанных средств, чтобы установить окно справки.


|**Версия SQL Server**|**Средства, устанавливающие окно справки**|**Версия установленного окна справки**|
|---------|---------|---------|
|SQL Server 2017<br>SQL Server 2016     |   [Последняя версия SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)<br><br>[Последняя версия SQL Server Data Tools для Visual Studio 2015](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)<br><br>Visual Studio 2017 (*поддерживает только SQL Server 2016*)  |  Версия 2.x       |
|SQL Server 2014    | SQL Server 2014 Management Studio<br><br>Версии Visual Studio, предшествующие Visual Studio 2012        |  Версия 1.x       |


> [!IMPORTANT]
> SQL Server 2016 устанавливает окно справки версии 1.1, которое нельзя использовать для просмотра документации по SQL Server 2016 и 2017.
> <br>
> <br>
> SQL Server 2017 не устанавливает окно справки.
> <br>
> <br>
> Чтобы установить окно справки с помощью Visual Studio 2017, откройте вкладку **Отдельные компоненты** в программе **Установщик Visual Studio**, выберите **Окно справки** в категории **Средства для работы с кодом** и нажмите кнопку **Установить**. 
> <br>
> <br>
> Вы можете просмотреть локальную справку для [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] с помощью окна справки версии 2.x, только если используете параметр **Установить содержимое с диска**. 


## <a name="sql-server-2016-sql-server-2017-offline-content"></a>Автономное содержимое для SQL Server 2016, SQL Server 2017  
 
**Установка автономного содержимого**  
1. Откройте окно справки версии 2.2, запустив SQL Server Management Studio или Visual Studio, а затем в меню **Справка** выберите пункт **Добавление и удаление содержимого справки**.  
2. Щелкните вкладку **Управление содержимым**.  
3. Чтобы установить справку из источника в Интернете, в области **источника установки** выберите **В сети**.  
![HelpViewer2_ManageContent_OnlineSource](../release-notes/media/helpviewer2-managecontent-onlinesource.png)  
7. Щелкните **Добавить** рядом с документацией, которую необходимо установить, а затем нажмите кнопку **Обновить**.  
![HelpViewer2_ManageContent_AddContent](../release-notes/media/helpviewer2-managecontent-addcontent.png)     
  
   >[!IMPORTANT] 
   >В SQL Server Management Studio и Visual Studio окно справки может перестать отвечать на запросы во время добавления документации. Чтобы устранить эту проблему, выполните указанные ниже действия. Сведения об этой проблеме см. в разделе [Окно справки Visual Studio зависает](https://msdn.microsoft.com/library/mt654096.aspx).  
   >>Откройте файл %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings в Блокноте и измените дату в приведенном ниже коде на какую-либо дату в будущем. Этот файл доступен на локальном компьютере, только если на нем установлена Visual Studio. 
   >>>Последнее обновление кэша: "12/31/2017 00:00:00".  
  
    Содержание в левой области автоматически обновится для добавления выбранной вами документации.  
![HelpViewer2_withContentInstalled](../release-notes/media/helpviewer2-withcontentinstalled.png)

1. (Необязательно). На вкладке **Управление содержимым** в поле **Путь к локальному хранилищу** отображается место установки документации на локальном компьютере. Чтобы переместить документацию в другое расположение, щелкните **Переместить**, в диалоговом окне **Перемещение содержимого** введите путь к папке в поле **В**, а затем нажмите кнопку **ОК**.

   ![Диалоговое окно HelpViewer2_Move Content](../release-notes/media/helpviewer2-move-content-dialog.png)

   После перемещения содержимого в поле **Local store path** (Путь к локальному хранилищу) отобразится новое расположение.
      
   >[!IMPORTANT]
   > Если вы получите уведомление о сбое операции перемещения, закройте окно сообщения и средство просмотра справки, а затем повторно откройте это средство. Теперь в поле **Local store path** (Путь к локальному хранилищу) вы должны увидеть новое расположение для содержимого.   
 
## <a name="includesssql14mdincludessssql14-mdmd-offline-content"></a>Автономное содержимое для [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] 
 
  
**Установка автономного содержимого**  
1. Чтобы скачать содержимое справки, перейдите на [сайт загрузки](https://www.microsoft.com/en-us/download/details.aspx?id=42557) и щелкните **Загрузить**.  
2. В окне сообщения щелкните **Сохранить**, чтобы сохранить файл SQLServer2014Documentation_*.exe на свой компьютер.  

 Для сред с брандмауэром и прокси-сервером сохраните загруженный файл на USB-накопитель или другой портативный носитель, который можно перенести в эти среды.   

3. Щелкните дважды EXE-файл, чтобы распаковать содержимое справки, и сохраните его в локальную или общую папку.  
4. Запустите SQL Server Management Studio или Visual Studio и в меню **Справка** щелкните **Управление параметрами справки**, чтобы открыть **диспетчер библиотек справки**.  
5. Щелкните **Установить содержимое с диска** и перейдите в папку, в которой находится распакованный файл с содержимым справки.  
  
     Выбор параметра "Установить содержимое с диска"  |Переход к файлу с содержимым справки   
     ---------|---------  
     ![HelpLibraryManager_MainPage_InstallFromDisk](../release-notes/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
     >[!IMPORTANT]
     > Используйте параметр **Установить содержимое с диска** в **диспетчере библиотек справки** для установки всего содержимого локальной справки.  
     >>Если же вы использовали параметр **Установить содержимое из Интернета** и средство просмотра справки отображает частичное содержимое, обратитесь к [этой записи блога](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/) для устранения неполадок. 

8. Щелкните файл HelpContentSetup.msha, выберите **Открыть**, а затем нажмите кнопку **Далее**.  
9. Щелкните **Добавить** рядом с документацией, которую необходимо установить, а затем нажмите кнопку **Обновить**.  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. Нажмите кнопку **Готово** и затем кнопку **Выйти**.
11. Снова откройте **Диспетчер библиотек справки**, щелкните пункт **Выберите справку в Интернете или локальную справку** и затем **I want to use local help** (Использовать локальную справку).
12. Откройте окно справки, чтобы просмотреть содержимое. Для этого в меню **Справка** щелкните **Просмотр справки**. В области слева в оглавлении вы должны увидеть установленное содержимое.  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../release-notes/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
## <a name="view-online-content-in-help-viewer"></a>Просмотр интернет-содержимого в окне справки

В окне справки версии 2.x вы можете просмотреть интернет-содержимое, выполнив одно из описанных ниже действий.

- В меню **Справка** SQL Server Management Studio щелкните **Просмотр справки**. Документация отобразится в браузере.
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)

- В меню **Справка** Visual Studio выберите пункт **Задать параметры справки** и щелкните **Запуск в браузере**. Когда вы щелкните **Просмотр справки** в меню **Справка**, в браузере отобразится документация.

![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)   

В окне справки версии 1.x вы можете просмотреть интернет-содержимое, выполнив описанные ниже действия.
1. В меню **Справка** щелкните **Управление параметрами справки**, чтобы открыть **диспетчер библиотек справки**.  
2. В диалоговом окне **диспетчера библиотек справки** щелкните **Выберите справку в Интернете или локальную справку**.  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../release-notes/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. Щелкните **I want to use online help** (Использовать справку в Интернете), нажмите кнопку **ОК** и выберите **Выйти**.  

   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../release-notes/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)

## <a name="f1-help-and-other-tips"></a>Справка F1 и другие советы

При нажатии клавиши F1 откроется соответствующий раздел справки в Интернете. В локальной справке таких разделов нет.

Кроме того, окно справки не поддерживает параметры прокси-сервера и формат ISO. 


## <a name="additional-information"></a>Дополнительные сведения
[Средство просмотра справки (Microsoft)](https://msdn.microsoft.com/library/hh580782.aspx)

