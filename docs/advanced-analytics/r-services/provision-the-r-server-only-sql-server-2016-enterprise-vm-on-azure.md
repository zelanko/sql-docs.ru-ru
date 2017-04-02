---
title: "Подготовка виртуальной машины SQL Server 2016 Enterprise только с R Server в Azure | Microsoft Docs"
ms.custom: ""
ms.date: "12/22/2016"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 5
---
# Подготовка виртуальной машины SQL Server 2016 Enterprise только с R Server в Azure

Виртуальная машина SQL Server 2016 Enterprise только с R Server в Azure — это новый способ быстрой и простой настройки серверной среды для поддержки решений R. Данная виртуальная машина Azure была предварительно настроена с использованием Microsoft R Server (изолированный). 

Эта новая виртуальная машина заменяет виртуальную машину RRE для Windows, которая была доступна в Azure Marketplace. 

Виртуальная машина также включает DeployR Enterprise для развертывания функций аналитики R внутри приложений и серверных систем. Дополнительные сведения см. в разделе [About Deploy R](https://msdn.microsoft.com/microsoft-r/deployr-about) (Сведения о развертывании R).


## Подготовка виртуальной машины R Server

Если вы не использовали виртуальные машины Azure раньше, рекомендуется ознакомиться с этой статьей, чтобы получить дополнительные сведения об использовании портала и настройке виртуальной машины.
[Виртуальные машины — приступая к работе](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)

Создание виртуальной машины R Server из Microsoft Azure Marketplace 
1. Щелкните **Виртуальные машины** и в поле поиска введите *R Server*.
2. Выберите **R Server Only SQL Server 2016 Enterprise**.
3. Продолжайте подготовку виртуальной машины, как описано в статье: [https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/). 
7. После создания и запуска виртуальной машины нажмите кнопку **Подключение**, чтобы установить подключение и войти на новую машину.
8. При подключении по умолчанию открывается **диспетчер серверов**, однако дополнительная настройка сервера не требуется. Закройте **диспетчер серверов**, чтобы вернуться на рабочий стол, и перейдите к следующим шагам.
    + Установка дополнительных средств R или средств разработки
    + Настройка DeployR  

Поиск виртуальной машины R Server на классическом портале Azure
1. Щелкните элемент **Виртуальные машины**, а затем нажмите кнопку **СОЗДАТЬ**.
2. В области **Создать** должны уже быть выбраны параметры **Вычисление** и **Виртуальная машина**. 
3. Щелкните **Из коллекции** для поиска образа виртуальной машины. Можно ввести *R Server* в поле поиска или щелкнуть **Microsoft** и затем прокрутить вниз до пункта **R Server Only SQL Server 2016 Enterprise**.


## Установка средств R
По умолчанию Microsoft R Server включает все средства R, устанавливаемые при базовой установке R, включая RTerm и RGui. На случай, если вы захотите сразу же приступить к использованию R, на рабочий стол был добавлен ярлык RGui.

Однако может потребоваться установить дополнительные средства R, например RStudio, средства R для Visual Studio или Microsoft R Client. Ниже приведены ссылки на расположения скачивания и инструкции:
+ [Средства R для Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio для Windows](https://www.rstudio.com/products/rstudio/download/)

После установки этих средств убедитесь, что ваши средства используют библиотеки R Server.

## Использование DeployR на виртуальной машине

Для использования экземпляра DeployR, установленного на виртуальной машине, требуется выполнить некоторые дополнительные действия. 

Настройка второго экземпляра DeployR:

1. На виртуальной машине откройте **служебную программы администратора DeployR**.
2. Задайте пароль администратора DeployR, как описано здесь:   [Шаги после установки](https://msdn.microsoft.com/microsoft-r/deployr-install-on-windows).
3. Задайте веб-контекст DeployR. Дополнительные сведения см. в разделе [DeployR Admin Installation in the Cloud](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud) (Установка DeployR в облаке). 
4. Откройте соответствующие порты на виртуальной машине, как описано здесь:   [Configuring Azure Endpoints](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#configuring-azure-endpoints) (Настройка конечных точек Azure). 
4. Обновите брандмауэр Windows, как описано здесь: [Updating the firewall](https://msdn.microsoft.com/microsoft-r/deployr-admin-install-in-cloud#updating-the-firewall) (Обновление брандмауэра). 

## Доступ к данным в учетной записи хранения Azure 

Если вам нужно использовать данные из своей учетной записи хранения Azure, существует несколько вариантов доступа к данным или их перемещения:


+ Скопируйте данные из вашей учетной записи хранения в локальную файловую систему с помощью служебной программы, например [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only). 

+ Добавьте файлы в общую папку в вашей учетной записи хранения и затем подключите ее как сетевой диск в виртуальной машине.  Дополнительные сведения см. в разделе [Mounting Azure files](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/) (Подключение файлов Azure). 

## Использование учетной записи хранилища Azure Data Lake Storage (ADLS)

Вы можете считывать данные из хранилища ADLS с помощью ScaleR, если ссылаетесь на учетную запись хранения таким же образом, как и на файловую систему HDFS, используя webHDFS.  Дополнительные сведения см. в этом [руководство по установке](http://go.microsoft.com/fwlink/?LinkId=723452).

## Ресурсы

Дополнительную документацию о Microsoft R можно найти в библиотеке MSDSN: [R Server and Scale R](https://msdn.microsoft.com/microsoft-r) (R Server и масштабирование R).  


См. следующие ресурсы с общими сведениями о R. 
+ [DataCamp](http://www.datacamp.com): предоставляет бесплатный курс начального и среднего уровня по R, а также курс по работе с большими данными с помощью Revolution R.
+ [Stack Overflow](http://www.stackoverflow.com): хороший ресурс с описанием программирования на R и использования средств ML. 
+ [Cross Validated](https://stats.stackexchange.com/): сайт с описанием трудностей статистического характера в машинном обучении.
+ [Архивы списков рассылки по справке для R](https://www.r-project.org/mail.html): хороший источник архивной информации. 
+ [Веб-сайт MRAN](https://mran.microsoft.com/documents/getting-started/): множество других ресурсов по R.  

## См. также:
[Службы R SQL Server](https://msdn.microsoft.com/library/mt604845.aspx)
