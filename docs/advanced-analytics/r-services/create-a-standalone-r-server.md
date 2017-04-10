---
title: "Создание изолированного сервера R Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 35
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# Создание изолированного сервера R Server
  Программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает возможность установить **Microsoft R Server (изолированную версию)**. Эта возможность позволяет разрабатывать высокопроизводительные решения R в Windows, подключаясь к любым базам данных или источникам данных. Microsoft R Server доступен только в выпуске Enterprise Edition.  
  
 При установке Microsoft R Server вы получаете тот же расширенный набор пакетов и средств подключения R, что и в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], но экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется, а скрипты R выполняются на изолированном компьютере, а не в базе данных.  
  
> [!NOTE]  
>  Microsoft R Server теперь поддерживает упрощенную процедуру установки, в процессе которой экземпляр регистрируется в политике [современного жизненного цикла](https://support.microsoft.com/help/447912). Такой вариант поддержки обеспечивает наличие наиболее актуальной версии R. Дополнительные сведения об использовании упрощенной процедуры установки см. в статье [Запуск Microsoft R Server для Windows](https://msdnstage.redmond.corp.microsoft.com/microsoft-r/rserver-install-windows?branch=r-server-nov16-dev).
>  
> Если вы устанавливаете Microsoft R Server посредством упрощенной процедуры установки, вы также можете преобразовать указанный экземпляр служб R для использования новой политики поддержки и более регулярного получения обновлений компонентов R. Дополнительные сведения см. в статье [Использование программы sqlBindR.exe для обновления экземпляра служб R](http://www.bing.com).   
  
##  <a name="a-namebkmkinstallrservicesindatabasea-install-microsoft-r-server-standalone"></a><a name="bkmk_installRServicesInDatabase"></a> Установка изолированного сервера Microsoft R Server  
  
1.  Если вы установили предыдущую версию Microsoft R Server, сначала необходимо удалить ее.  См. раздел [Обновление с предыдущей версии Microsoft R Server](#bkmk_Uninstall). 

2. Запустите программу установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  На вкладке **Установка** щелкните **New R Server (Standalone) installation** (Установка нового изолированного сервера R).  
  
     ![Setup option for R Server Standalone](../../advanced-analytics/r-services/media/rsql-rstandalonesetup.png "Setup option for R Server Standalone")  
  
3.  На странице **Выбор компонентов** уже должен быть выбран следующий параметр:  
  
    -   **R Server (изолированный)**  
  
         Этот параметр устанавливает общие компоненты, включая инструменты R с открытым исходным кодом и базовые пакеты, а также улучшенные пакеты R и инструменты подключения, предоставляемые Microsoft R.  
  
     Все прочие параметры можно игнорировать.  
  
4.  Примите условия лицензии, чтобы скачать и установить Microsoft R Open. Когда кнопка **Принять** станет недоступна, можно нажать кнопку **Далее**. Установка этих компонентов (и всех необходимых компонентов, которые могут потребоваться) может занять некоторое время.   
  
5.  На странице **Все готово для установки** проверьте выбранные параметры и нажмите кнопку **Установить**.  
  
> [!TIP]
> Дополнительные сведения об автоматической или автономной установке см. в разделе [Установка Microsoft R Server из командной строки](../../advanced-analytics/r-services/install-microsoft-r-server-from-the-command-line.md).

  
## <a name="what-is-installed-and-where-to-find-r-packages"></a>Устанавливаемые компоненты и расположение пакетов R  
 Microsoft R Server включает в себя базовые пакеты R и набор расширенных пакетов R, которые поддерживают параллельную обработку, а также оптимизируют производительность и подключение к источникам данных, включая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и Hadoop.  
  
-   **Пакеты R**  
  
     Библиотеки R устанавливаются вместе с другими средствами и служебными программами в составе Microsoft SQL Server 2016. Например:  
  
     `C:\Program Files\Microsoft SQL Server\130\R_SERVER`  
  
     Кроме того, в этой папке находятся образцы данных и документация по базовым пакетам, средствам и среде выполнения R.  
  
    > [!NOTE]  
    >  Если вы установили экземпляр SQL Server и службы R (в базе данных) на одном компьютере, библиотеки и средства R устанавливаются в другой папке: `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`.  
    >   
    >  Не используйте пакеты или служебные программы R, связанные с экземпляром [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Всегда используйте средства и пакеты R из папки R_SERVER.  
  
-   **Средства R**  
  
     Интегрированная среда разработки R не устанавливается программой установки. Вы можете установить RStudio, [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] или любую другую среду разработки на свой выбор.  
  
     Но дополнительные средства не требуются. Все стандартные базовые средства R входят в состав `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin`.  
  
     Дополнительные сведения см. в разделе [Установка или настройка средств R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md).  


 
## <a name="troubleshooting"></a>Устранение неполадок  

### <a name="incompatible-version-of-r-client-and-r-server"></a>Несовместимые версии клиента R и сервера R Server

Если вы установили последнюю версию клиента Microsoft R и используете ее для выполнения R в SQL Server с помощью удаленного контекста вычисления, может возникнуть следующая ошибка:

*На компьютере используется версия 9.0.0 клиента Microsoft R, которая несовместима с Microsoft R Server версии 8.0.3. Скачайте и установите совместимую версию*.

Как правило, версия R, устанавливаемая со службами SQL Server R, обновляется при публикации выпусков служб. Чтобы обеспечить наличие самых актуальных версий компонентов R, установите все пакеты обновления. Для совместимости с клиентом Microsoft R 9.0.0 необходимо установить обновления, которые описываются в этой [статье службы поддержки](https://support.microsoft.com/kb/3210262). 


### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Установка Microsoft R Server в экземпляре SQL Server, установленном в Windows Server Core
В версии выпуска SQL Server 2016 имелась известная проблема при добавлении Microsoft R Server в экземпляр в выпуске Windows Server Core. Эта ошибка исправлена. 

При ее возникновении можно применить исправление, описываемое в [статье 3164398 базы знаний](https://support.microsoft.com/kb/3164398), чтобы добавить компонент R в существующий экземпляр в Windows Server Core.   Дополнительные сведения см. в разделе [Не удается установить изолированный сервер Microsoft R Server в операционной системе Windows Server Core](https://support.microsoft.com/kb/3168691).


###  <a name="a-namebkmkuninstalla-upgrading-from-an-older-version-of-microsoft-r-server"></a><a name="bkmk_Uninstall"></a> Обновление с предыдущей версии Microsoft R Server  
 Если вы установили предварительную версию Microsoft R Server, ее необходимо удалить перед обновлением до более новой версии.  
  
**Удаление изолированного сервера R Server**  
  
1.  В **панели управления** щелкните элемент **Установка и удаление программ**, а затем выберите `Microsoft SQL Server 2016 <version number>`.  
  
2.  В диалоговом окне с командами **добавления**, **восстановления** и **удаления** компонентов выберите **Удалить**.  
  
3.  На странице **Выбор компонентов** в разделе **Общие компоненты** выберите **R Server (изолированный)**. Нажмите кнопку **Далее**, а затем — кнопку **Готово**, чтобы удалить только выбранные компоненты.  
   
### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>Установка завершается ошибкой "Одновременная установка нескольких продуктов Revolution Enterprise невозможна".  
Эта ошибка может возникнуть, если у вас уже установлены продукты Revolution Analytics или предварительная версия служб SQL Server R. Перед тем как устанавливать новую версию Microsoft R Server, необходимо удалить все предыдущие версии. Параллельная установка с другими версиями средств Revolution Enterprise не поддерживается.  

Но она поддерживается при использовании изолированного сервера R Server с [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и 
  
### <a name="unable-to-uninstall-older-components"></a>Не удается удалить старые компоненты.   
  
Если у вас возникают проблемы с удалением предыдущей версии, вам может потребоваться отредактировать реестр, удалив соответствующие разделы.  

> [!IMPORTANT]
> Эта проблема возникает, только если вы установили предварительную версию Microsoft R Server или версию CTP служб SQL Server 2016 R.
  
1. Откройте реестр Windows и найдите следующий раздел: `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`.  
2. Удалите следующие записи, если они имеются и если раздел содержит только параметр `sEstimatedSize2`:  
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (для версии 8.0.2)  
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (для версии 8.0.1)  
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (для версии 8.0.0)  
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (для версии 7.5.0)  
  
## <a name="see-also"></a>См. также  
 [Microsoft R Server](../../advanced-analytics/r-services/r-server-standalone.md)  
  
  