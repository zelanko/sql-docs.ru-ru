---
title: "Поставщики данных, используемые для соединений служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 51b41114385321e84511c188077e48455d1678a2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="data-providers-used-for-analysis-services-connections"></a>Поставщики данных, используемые для соединений со службами Analysis Services
  Службы Analysis Services предоставляют 3 поставщика данных для сервера и доступа к данным. Все приложения подключаются к службам Analysis Services с помощью одного из следующих поставщиков. Два из этих поставщиков, ADOMD.NET и управляющие объекты AMO служб Analysis Services, — управляемые поставщики данных. Поставщик OLE DB для служб Analysis Services (MSOLAP DLL) является собственным поставщиком данных.  
  
 В организациях, где работает несколько версий служб Analysis Services, может потребоваться установка более свежих версий поставщиков данных на пользовательских рабочих станциях, подключающихся к данным служб Analysis Services. Для подключения к более новым версиям служб Analysis Services необходимы поставщики данных из того же основного выпуска. Например, для подключения к службам [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]на каждой рабочей станции должен быть установлен поставщик данных из того же выпуска. Несмотря на то что Excel устанавливает поставщиков данных, которые нужны программе для подключения, поставщик часто имеет более старую версию по сравнению с используемыми экземплярами служб Analysis Services.  
  
 Этот раздел состоит из следующих подразделов.  
  
 [Как определить версию сервера](#bkmk_ServVers)  
  
 [Как определить версию поставщиков данных служб Analysis Services](#bkmk_LibUpdate)  
  
 [Получение обновленной версии поставщиков данных](#bkmk_downloadsite)  
  
 [Поставщик OLE DB служб Analysis Services](#bkmk_OLE)  
  
 [ADOMD.NET](#bkmk_ADOMD)  
  
 [AMO](#blkmk_AMO)  
  
##  <a name="bkmk_ServVers"></a> Как определить версию сервера  
 Сведения о версии экземпляра служб Analysis Services позволяют определить, нужно ли устанавливать более новые версии поставщиков данных на рабочих станциях в организации.  
  
-   Установите соединение с экземпляром служб Analysis Services в среде SQL Server Management Studio. Данные о версии см. в меню **Свойства сервера** > **Общие** > **Версия**.  
  
 Номер основной сборки первоначального выпуска [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] — 13.0.1601.5.  
  
  
##  <a name="bkmk_LibUpdate"></a> Как определить версию поставщиков данных служб Analysis Services  
 Поставщики данных устанавливаются со службами Analysis Services, а также клиентскими приложениями, которые регулярно подключаются к базам данных служб Analysis Services, таким как Excel.  
  
 Office 2010 устанавливает поставщики данных из SQL Server 2008. Office 2013 устанавливает поставщиков данных из SQL Server 2012 и т. д. Если используется несколько версий Office или SQL Server, а доступность соединений или функций не соответствует ожиданиям, то, по-видимому, необходимо установить более новую версию поставщиков данных. На одном компьютере можно одновременно установить несколько основных версий каждого поставщика данных.  
  
#### <a name="find-the-file-version-of-the-oledb-provider"></a>Определение версии поставщика OLEDB  
  
1.  Перейдите в каталог \Program Files\Microsoft Analysis Services\AS OLEDB\130.  
  
2.  Щелкните правой кнопкой мыши **msolap130.dll** > **Свойства** > **Сведения**.  
  
 Если в этом местоположении нет файла либо если в пути к папке содержится «AS OLEDB\110» или «AS OLEDB\90», то используется старая библиотека и для подключения к [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]необходимо установить более новую версию (AS OLEDB\11).  
  
#### <a name="find-the-file-version-of-adomdnet-and-amo"></a>Определение версии ADOMD.NET и объектов AMO  
  
1.  Перейдите к папке «C:\Windows\Assembly»  
  
2.  Щелкните правой кнопкой мыши файл Microsoft.AnalysisServices.AdomdClient и выберите **Свойства**. Нажмите **Версия**.  
  
     Применительно к объектам AMO щелкните правой кнопкой мыши Microsoft.AnalysisServices.  
  
##  <a name="bkmk_downloadsite"></a> Получение обновленной версии поставщиков данных  
 Версия, установленная на клиентском компьютере, должна совпадать с основной версией сервера, поставляющего данные. Если установка сервера более новая, чем у поставщиков данных, установленных на рабочих станциях в сети, может потребоваться установить новые библиотеки.  
  
#### <a name="find-the-data-providers-on-the-download-site"></a>Поиск поставщиков данных на сайте загрузок  
  
1.  Перейдите в [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=52676).  
  
2.  Нажмите кнопку **Загрузить**. ADOMD.NET, поставщик OLE DB и объекты AMO, включаются в список как устанавливаемый пакет. Например, SQL_AS_OLEDB.msi. Каждая библиотека имеет 32- или 64-разрядную версию. Для серверов и новых рабочих станций, работающих под управлением 64-разрядной операционной системы, потребуется 64-разрядная версия.  
  
##  <a name="bkmk_OLE"></a> Поставщик OLE DB служб Analysis Services  
 Поставщик Analysis Services OLE DB — это собственный поставщик для подключения к базе данных Analysis Services. Как ADOMD.NET, так и объекты AMO косвенно используют MSOLAP, делегируя запросы соединений поставщику данных. Можно также вызвать поставщик OLE DB непосредственно из кода приложения, если требования к решению исключают использование управляемого API-интерфейса.  
  
 Поставщик Analysis Services OLE DB устанавливается автоматически программами установки SQL Server, Excel и других приложений, которые часто используются для осуществления доступа к базам данных служб Analysis Services. Его также можно установить вручную, загрузив поставщик из центра загрузки. По умолчанию поставщик находится в папке \Program Files\Microsoft Analysis Services. Поставщик должен быть установлен на любой рабочей станции, используемой для получения доступа к данным служб Analysis Services.  
  
 MSOLAP130.dll — это версия поставщика OLE DB служб Analysis Services, которая поставляется в составе [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. К другим более ранним версиям относятся MSOLAP110.dll (для SQL Server 2008 и 2008 R2) и MSOLAP90.dll (для SQL Server 2005).  
  
 Поставщики OLE DB часто указываются в строках подключения. Строка подключения служб Analysis Services используется другая спецификация для ссылки на поставщик OLE DB: MSOLAP. \<версия > .dll  
  
 MSOLAP.5.dll — это текущий поставщик Analysis Services OLE DB, устанавливаемый в составе Excel 2013. На рабочих станциях, где работают более старые версии Excel, часто можно найти предыдущие версии, например MSOLAP.4.dll или MSOLAP.3.dll. Для некоторых компонентов служб Analysis Services, таких как надстройка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], требуются определенные версии поставщика OLE DB. Дополнительные сведения см. в разделе [Свойства строки подключения (службы Analysis Services)](../../analysis-services/instances/connection-string-properties-analysis-services.md).  
  
##  <a name="bkmk_ADOMD"></a> ADOMD.NET  
 ADOMD.NET — управляемый поставщик данных, который используется для запроса данных из служб Analysis Services. Excel использует ADOMD.NET при подключении к определенному кубу служб Analysis Services. Строка подключения в Excel предназначена для подключения ADOMD.NET.  
  
 Компонент ADOMD.NET устанавливается программой установки SQL Server и используется клиентскими приложениями SQL Server для подключения к службам Analysis Services. Эта библиотека устанавливается в Office для поддержки подключения к данным из Excel. Как и в случае с другими поставщиками данных, входящими в состав SQL Server, если программист использует библиотеку в пользовательском коде, то может распространять ADOMD.NET самостоятельно. Можно также загрузить и установить ее вручную, чтобы получить более новую версию (см. подраздел [Как определить версию поставщиков данных служб Analysis Services](#bkmk_LibUpdate) этого раздела).  
  
 Для проверки информации о версии файла найдите ADOMD.NET в глобальном кэше сборок, где эта библиотека указана как `Microsoft.AnalysisServices.AdomdClient`.  
  
 При подключении к базе данных свойства строки подключения для всех трех библиотек во многом совпадают. Почти любая строка подключения, заданная для ADOMD.NET (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>), применима также для AMO и поставщика Analysis Services OLE DB. Дополнительные сведения см. в разделе [Свойства строки подключения (службы Analysis Services)](../../analysis-services/instances/connection-string-properties-analysis-services.md).  
  
 Дополнительные сведения о подключении программным путем см. в разделе [Establishing Connections in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md).  
  
##  <a name="blkmk_AMO"></a> AMO  
 Объекты AMO — это управляемый поставщик данных, используемый для администрирования сервера и определения данных. Например, объекты AMO используются в среде SQL Server Management Studio для подключения к службам Analysis Services.  
  
 Объекты AMO устанавливаются программой установки SQL Server и используются клиентскими приложениями SQL Server для подключения к службам Analysis Services. Можно также загрузить и установить объекты AMO вручную для применения в пользовательском коде (см. подраздел [Как определить версию поставщиков данных служб Analysis Services](#bkmk_LibUpdate) этого раздела). Объекты AMO можно найти в глобальном кэше сборок под названием `Microsoft.AnalysisServices`.  
  
 Подключение с помощью объектов AMO обычно минимально и состоит из «источник данных =\<имя_сервера >». После того как соединение установлено, используется API-интерфейс для работы с коллекциями и основными объектами базы данных. Как SSDT, так и SSMS используют объекты AMO для подключения к экземпляру служб Analysis Services.  
  
 Дополнительные сведения о подключении программным путем см. в разделе [Programming AMO Fundamental Objects](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md).  
  
## <a name="see-also"></a>См. также  
 [Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
