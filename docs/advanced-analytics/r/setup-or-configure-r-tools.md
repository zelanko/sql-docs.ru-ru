---
title: "Установка или настройка средств R | Документация Майкрософт"
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3baf97a960d7e8f950bb6e9cd251550f4c4b942
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="setup-or-configure-r-tools"></a>Установка или настройка средств R
  Microsoft R Server предоставляет все базовые библиотеки R, набор пакетов ScaleR и стандартные средства R, необходимые для разработки и тестирования кода R. Кроме того, также доступны средства, в том числе бесплатные, и для выделенной среды разработки R.  
  
## <a name="basic-r-tools"></a>Базовые средства R  
 При установке Microsoft R Server дополнительные средства не требуются, так как все стандартные средства R, включенные в *базовую установку* R, устанавливаются по умолчанию.

-   **RTerm** — средство командной строки для выполнения скриптов R. 
  
-   **RGui.exe** — простой интерактивный редактор для R. Аргументы командной строки для RGui.exe и RTerm одни и те же. 
  
-   **RScript** — средство командной строки для выполнения скриптов R в пакетном режиме.  

Чтобы найти эти средства, необходимо найти расположение библиотеки R. Установленные средства зависят от того, установили ли вы только службы R SQL Server или еще и R Server (изолированную версию). Дополнительные сведения см. в разделе [Устанавливаемые компоненты и расположение пакетов R](https://msdn.microsoft.com/library/mt695941(sql.130).aspx#Anchor_1).

Затем поищите в папке `..\R_SERVER\bin\x64`.  

> [!TIP]  
>  Нужна помощь со средствами R? В папках программы установки `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` и `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual` содержится документация по использованию средств R.  
>   
>  Или вы можете просто открыть **RGui**, щелкнуть **Справка**, а затем выбрать какой-либо из вариантов.  

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R Client можно скачать бесплатно. Он позволяет разрабатывать решения R, легко выполняющиеся на Microsoft R Server или в службах R SQL Server. Он предусмотрен, чтобы помочь специалистам по обработке и анализу данных, у которых нет доступа к службам R Server (доступным в Enterprise Edition), разрабатывать решения, использующие ScaleR. 

Если вы используете другую среду разработки R, например средства R для Visual Studio или RStudio, то чтобы использовать ScaleR, вы должны указать, что Microsoft R Client будет использоваться в качестве исполняемого объекта R. Это предоставит полный доступ к пакету RevoScaleR и другим функциям Microsoft R Server, но производительность будет ограничена.

Вы также можете использовать средства в R Client, например RGui и RTerm, для запуска скриптов или написания и выполнения нерегламентированного кода R.

[Установка Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="bkmk_RTools"></a>Средства R для Visual Studio  

 Чтобы было удобно работать с базами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] в качестве среды разработки. [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] — это бесплатная надстройка для Visual Studio, которая поддерживается во всех выпусках. Visual Studio также поддерживает интеграцию языков Python и F#.  

 Инструкции по установке см. в разделе [установке средств R для Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).

> [!TIP]
> Прежде чем установить какие-либо новые пакеты, проверьте, какая среда выполнения R используется по умолчанию. Если этого не сделать, вы сможете очень просто установить новые пакеты R в расположение библиотеки по умолчанию, но не сможете найти их с помощью R Server.


## <a name="rstudio"></a>RStudio

Если вы предпочитаете RStudio, для использования библиотек RevoScaleR вам потребуется выполнить некоторые дополнительные действия.
- Установите Microsoft R Server или Microsoft R Client, чтобы получить необходимые пакеты и библиотеки.
- Укажите в пути к R среду выполнения R Server.

Дополнительные сведения см. в разделе о [настройке интегрированной среды разработки](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).


## <a name="see-also"></a>См. также:  
 [Создание изолированного сервера R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Приступая к работе с изолированным сервером Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  

