---
title: "Средство просмотра справки для SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fc2435ccea3b01328c3c4623e62fbf12ee53e400
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="help-viewer-for-sql-server"></a>Средство просмотра справки для SQL Server
  
  
  
В этой статье вы узнаете, как установить локальную справку, а также открыть эту справку и справку в Интернете. Здесь рассматривается средство просмотра справки Microsoft 1.1 и 2.2, а также документация для [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] и [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]. 

>[!IMPORTANT]
>Средство просмотра справки не поддерживает параметры прокси-сервера и формат ISO.  

>**Открытие справки с помощью клавиши F1**
>>При нажатии клавиши F1 откроется соответствующий раздел справки в Интернете. В локальной справке таких разделов нет.

## <a name="includesscurrentmdincludessscurrent-mdmd-and-help-viewer-22"></a>[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] и средство просмотра справки 2.2  
Средство просмотра справки 2.2 доступно в Visual Studio 2015 и Management Studio для [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], начиная с предварительной версии за апрель 2016 г. (13.0.12500.29).  

> [![Скачать SSMS](../release-notes/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Скачайте последнюю версию SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**  

**Чтобы установить локальную справку с использованием средства просмотра справки 2.2:**  
1. Откройте средство просмотра справки 2.2. Для этого запустите SQL Server Management Studio или Visual Studio, а затем в меню **Справка** щелкните **Добавление и удаление содержимого справки**.  
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

1. (Необязательно.) На вкладке **Управление содержимым** в поле **Local store path** (Путь к локальному хранилищу) отобразится расположение установки документации на локальном компьютере. Чтобы переместить документацию в другое расположение, щелкните **Переместить**, в диалоговом окне **Перемещение содержимого** введите путь к папке в поле **В**, а затем нажмите кнопку **ОК**.

   ![Диалоговое окно HelpViewer2_Move Content](../release-notes/media/helpviewer2-move-content-dialog.png)

   После перемещения содержимого в поле **Local store path** (Путь к локальному хранилищу) отобразится новое расположение.
      
   >[!IMPORTANT]
   > Если вы получите уведомление о сбое операции перемещения, закройте окно сообщения и средство просмотра справки, а затем повторно откройте это средство. Теперь в поле **Local store path** (Путь к локальному хранилищу) вы должны увидеть новое расположение для содержимого.   
  
**Чтобы отобразить локальную справку или справку в Интернете в SQL Server Management Studio:**  
* Чтобы просмотреть локальную справку, в меню **Справка** щелкните **Добавление и удаление содержимого справки**, а затем выберите вкладку **Начальная страница окна справки**, где можно просмотреть документацию.  
    >[!NOTE]
    >Текст **начальной страницы окна справки** изменяется в зависимости от раздела, который вы выбираете в содержании.   
* Чтобы просмотреть справку в Интернете, в меню **Справка** щелкните **Просмотр справки**. Документация отобразится в браузере.  
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)  
  
  
**Чтобы отобразить локальную справку или справку в Интернете в Visual Studio:**  
* В меню **Справка** щелкните **Задать параметры справки** и выполните одно из приведенных ниже действий.  
   * Щелкните **Запустить в браузере**, чтобы просмотреть справку в Интернете. Когда вы щелкните **Просмотр справки** в меню **Справка**, в браузере отобразится документация.  
   * Щелкните **Запустить в средстве просмотра справки**, чтобы просмотреть локальную справку. Когда вы щелкните **Просмотр справки** в меню **Справка**, в средстве просмотра справки отобразится документация.  
     
     ![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)  
  
  
## <a name="includesssql14mdincludessssql14-mdmd-and-help-viewer-11"></a>[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] и средство просмотра справки 1.1  
 Средство просмотра справки 1.1 доступно в [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] Management Studio и версиях Visual Studio, предшествующих Visual Studio 2012.   
 
>[!NOTE]
> Вы также сможете просмотреть локальную справку для [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] с помощью средства просмотра справки 2.2, если **установите содержимое с диска**. Средство просмотра справки 2.2 доступно в Visual Studio 2015 и Management Studio для [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], начиная с предварительной версии за апрель 2016 г. (13.0.12500.29). 
   
**Чтобы установить локальную справку с использованием средства просмотра справки 1.1:**  
1. Чтобы скачать содержимое справки, перейдите на [сайт загрузки](https://www.microsoft.com/en-us/download/details.aspx?id=42557) и щелкните **Загрузить**.  
2. В окне сообщения щелкните **Сохранить**, чтобы сохранить файл SQLServer2014Documentation_*.exe на свой компьютер.  
   >[!NOTE]
   >Для сред с брандмауэром и прокси-сервером сохраните загруженный файл на USB-накопитель или другой портативный носитель, который можно перенести в эти среды.   
3. Щелкните дважды EXE-файл, чтобы распаковать содержимое справки, и сохраните его в локальную или общую папку.  
4. Запустите SQL Server Management Studio или Visual Studio и в меню **Справка** щелкните **Управление параметрами справки**, чтобы открыть **диспетчер библиотек справки**.  
7. Щелкните **Установить содержимое с диска** и перейдите в папку, в которой находится распакованный файл с содержимым справки.  
  
Выбор параметра "Установить содержимое с диска"  |Переход к файлу с содержимым справки   
---------|---------  
![HelpLibraryManager_MainPage_InstallFromDisk](../release-notes/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
>[!IMPORTANT]
> Используйте параметр **Установить содержимое с диска** в **диспетчере библиотек справки** для установки всего содержимого локальной справки.  
>>Если же вы использовали параметр **Установить содержимое из Интернета** и средство просмотра справки отображает частичное содержимое, обратитесь к [этой записи блога](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/) для устранения неполадок. 

8. Щелкните файл HelpContentSetup.msha, выберите **Открыть**, а затем нажмите кнопку **Далее**.  
9. Щелкните **Добавить** рядом с документацией, которую необходимо установить, а затем нажмите кнопку **Обновить**.  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. Нажмите кнопку **Готово**, а затем — **Выход**. Откройте средство просмотра справки, чтобы просмотреть содержимое. Для этого в меню **Справка** щелкните **Просмотр справки**. В области слева в оглавлении вы должны увидеть установленное содержимое.  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../release-notes/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
**Чтобы отобразить локальную справку или справку в Интернете:**  
1. В меню **Справка** щелкните **Управление параметрами справки**, чтобы открыть **диспетчер библиотек справки**.  
2. В диалоговом окне **диспетчера библиотек справки** щелкните **Выберите справку в Интернете или локальную справку**.  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../release-notes/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. Выполните одно из приведенных ниже действий, а затем нажмите кнопку **ОК** и щелкните **Выход**.  
   * Установите переключатель **I want to use online help** (Использовать справку в сети).  
   * Установите переключатель **I want to use local help** (Использовать локальную справку).  
  
   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../release-notes/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)  
  
Если вы выберите использование справки в сети, при выборе **Просмотр справки** в меню **Справка** в браузере отобразится статья на MSDN [Электронная документация по SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx). Если вы выберите использование локальной справки, при выборе **Просмотр справки** отобразится средство просмотра справки.  

## <a name="additional-information"></a>Дополнительные сведения
[Средство просмотра справки (Microsoft)](https://msdn.microsoft.com/library/hh580782.aspx)

