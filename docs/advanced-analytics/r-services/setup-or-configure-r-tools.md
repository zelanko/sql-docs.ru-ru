---
title: "Установки или настройки средств R | Microsoft Docs"
ms.custom: ""
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Установки или настройки средств R
  R Microsoft Server предоставляет все базовые библиотеки R, пакеты R масштабирования и стандартная R средства, необходимые для разработки и тестирования кода R. Тем не менее если вы хотите использовать выделенный среду разработки R, существует несколько доступных, в том числе многих бесплатных средств.  
  
## <a name="basic-r-tools"></a>R основные средства  
 Дополнительные средства не требуются при установке Microsoft R Server, поскольку все стандартные R средств, включенных в *базового установки* R устанавливаются по умолчанию.

-   **RTerm**: средство командной строки для выполнения скриптов R 
  
-   **RGui.exe**: простой интерактивный редактор для языка R. Аргументы командной строки одинаковы для RGui.exe и RTerm. 
  
-   **RScript**: средство командной строки для запуска R сценарии в пакетном режиме.  

По умолчанию эти средства устанавливаются в следующие папки:
- SQL Server 2016: `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64`  
- VNext SQL Server: `C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64`  

> [!TIP]  
>  Требуется дополнительная помощь? В документации по инструментам R можно найти в папке установки: `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` и `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual`.  
>   
>  Или просто откройте **RGui**, нажмите кнопку **помочь**, и выберите один из вариантов.  

## <a name="microsoft-r-client"></a>Microsoft R Client

Клиент Microsoft R — бесплатной загрузки, который позволяет разрабатывать решения R, которые можно легко запускать на сервере R или R служб SQL Server.

Обычно установите другую среду разработки R, например R средства для Visual Studio или RStudio и затем указать, что клиент Microsoft R используется исполняемый файл R. Это дает полный доступ к пакету RevoScaleR и другие возможности Microsoft R Server.

Также можно использовать знакомые средства, такие как RGui и RTerm для запуска скриптов или запись и выполнение нерегламентированных кода R.

[Установка клиента Microsoft R](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="a-namebkmkrtoolsa-r-tools-for-visual-studio"></a> R средства для Visual Studio  

 Для удобства в работе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных, рассмотрите возможность использования [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] как среду разработки. [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] — Бесплатная надстройка для Visual Studio, которая работает во всех выпусках Visual Studio. Visual Studio также предоставляет поддержку для интеграции F # и Python.  

Дополнительные сведения см. в разделе [VisualStudio.com](https://www.visualstudio.com/vs/rtvs/).

 В этом разделе описывается установка [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] с помощью бесплатной Community Edition из Visual Studio.  
  
#### <a name="install-visual-studio"></a>Установка Visual Studio  
  
1.  Бесплатный выпуск сообщества Visual Studio доступен для загрузки на этой странице: [Visual Studio Community](http://visualstudio.com/products/visual-studio-community-vs.aspx)  
  
2.  После завершения загрузки нажмите кнопку **запуска** и выберите компоненты для установки.  
  
     При выполнении выборочной установки, обратите внимание, что требуются компоненты Microsoft Web Developer.  
  
3.  Выберите **Общие** параметр на данный момент. При установке [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], вы получите toption, чтобы изменить макет, настроенные для разработки R.  

#### <a name="add-the-r-tools"></a>Добавление средств R

После установки Visual Studio расширения доступны для R, Python и многих других языков через **Параметры** меню.

4. Выберите в меню Сервис в строке меню, а затем выберите **расширения и обновления**.

5. В конце установки средства R обнаружит версии среды выполнения R, доступные на компьютере и попросите, если вы хотите изменить среду разработки для использования исполняющей среды R для сервера Microsoft R или R среда выполнения клиента Microsoft R.

Если программа установки обнаружит выполнения R сервера, необходимо использовать, можно изменить его вручную в любое время с помощью **Параметры** меню. Дополнительные сведения см. в разделе [настроить ваш IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).

## <a name="rstudio"></a>RStudio

Если вы предпочитаете использовать RStudio, выполните следующие дополнительные действия для использования библиотек RevoScaleR.
- Установите Microsoft R Server или R клиент Microsoft для получения необходимых пакетов и библиотек.
- Обновите путь к R использование соответствующих R среды выполнения.

Дополнительные сведения см. в разделе [настроить ваш IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).


## <a name="see-also"></a>См. также:  
 [Создание автономного сервера R](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Приступая к работе с сервером Microsoft R &#40; Автономные &#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  