---
title: "Установка поставщиков данных служб Analysis Services (AMO, ADOMD.NET, MSOLAP) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7aedabc-6af9-4698-a7a4-98f894001476
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bd6aa812228cce132b4180a8537ba853f3ea92a2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="install-analysis-services-data-providers-amo-adomdnet-msolap"></a>Установка поставщиков данных для служб Analysis Services (AMO, ADOMD.NET, MSOLAP)
  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] содержит обновление поставщиков данных для служб Analysis Services, к которым относятся ADOMD.Net, AMO и MSOLAP.  
  
 В большинстве сценариев доступа к данным на основе запросов вы можете продолжать использовать старые версии поставщиков данных, которые уже установлены на клиентских компьютерах, для доступа к табличным и многомерным моделям в экземпляре служб Analysis Services для SQL Server 2016. Это относится и к табличным моделям, которые используют функции, появившиеся в SQL Server 2016. Как правило, клиентским приложениям, которые создают запросы, например Excel, Reporting Services или Tableau, не нужен новейший поставщик данных для доступа к модели служб Analysis Services.  
  
 Средства моделирования и администрирования являются исключением из правила, по крайней мере с точки зрения требований к версии поставщиков данных. Чтобы эти средства могли управлять объектами на сервере, им необходимы поставщики данных, созданные специально для целевого сервера. К счастью, средства, поставляемые вместе с [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , уже включают поставщики данных, которые соответствуют текущей версии сервера.  При установке SQL Server Data Tools для Visual Studio 2015 также устанавливаются поставщики данных служб Analysis Services для SQL Server 2016. Точно так же при установке среды Management Studio для SQL Server 2016, которая использует объекты AMO и ADOMD.Net, устанавливаются оба поставщика данных для [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Единственный случай, когда требуется ручная установка поставщика данных — это пользовательские приложения или сценарии, использующие объекты управления Analysis Services (AMO). В этой версии реорганизовано пространство имен, в котором перемещены многие основные объекты. Например, Server и Database перемещены в новое пространство имен (Microsoft.AnalysisServices.Core), являющееся частью сборки Microsoft.AnalysisServices.dll. Если вы создали пользовательский код или сценарии, использующие объекты AMO, вам потребуется повторно скомпилировать код и обновить объекты AMO вручную на каждом сервере и клиентской рабочей станции, которая напрямую подключается к экземпляру служб Analysis Services для SQL Server 2016 через объекты AMO.  
  
## <a name="provider-list"></a>Список поставщиков  
 В следующей таблице описаны все поставщики.  
  
||||  
|-|-|-|  
|Поставщик|Имя файла|Версия|  
|Управляющие объекты служб Analysis Services (AMO)|Microsoft.AnalysisServices.dll|13.0.0.0|  
|Ядро Analysis Services|Microsoft.AnalysisServices.Core.dll|13.0.0.0|  
|Службы Analysis Services (ADOMD.NET)|Microsoft.AnalysisServices.AdomdClient.dll|13.0.0.0|  
|Поставщик OLE DB для служб Analysis Services (MSOLAP)|MSOLAP130.dll|13.0.0.0|  
  
## <a name="download-and-install-data-provider"></a>Скачивание и установка поставщика данных  
  
1.  Перейдите на страницу загрузки [пакета дополнительных компонентов SQL Server 2016](http://go.microsoft.com/fwlink/?LinkID=398150).  
  
2.  Щелкните **Загрузить** , чтобы выбрать установку отдельных компонентов.  
  
3.  Для 64-разрядных компьютеров выберите все или некоторые из следующих пакетов (аналогично, для 32-разрядных компьютеров выберите соответствующие элементы):  
  
    -   ENU\x64\SQL_AS_ADOMD.msi  
  
    -   ENU\x64\SQL_AS_AMO.msi  
  
    -   ENU\x64\SQL_AS_OLEDB.msi  
  
4.  Щелкните **Далее** , чтобы загрузить файлы.  
  
5.  По очереди запустите приложения, чтобы установить поставщики. Сборки ADO.MD и AMO устанавливаются в папку C:\Windows\assembly\GAC_MSIL. Поставщик OLE DB для служб Analysis Services устанавливается в папку C:\Program Files\Microsoft Analysis Services\AS OLEDB\130.  
  
## <a name="verify-installation"></a>Проверка установки  
  
1.  В проводнике перейдите в папку C:\Windows\Assembly.  
  
2.  Щелкните правой кнопкой мыши файл Microsoft.AnalysisServices и выберите пункт **Свойства**.  
  
3.  Выберите пункт **Версии** и убедитесь, что вы установили последнюю сборку.  
  
  

