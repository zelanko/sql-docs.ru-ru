---
title: Требования к архитектуре клиента для разработки Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- local mining models [Analysis Services]
- Analysis Services, architecture
- providers [Analysis Services]
- data pumps [Analysis Services]
- client architecture [Analysis Services]
- local cubes [Analysis Services]
ms.assetid: 03a8eb6b-159f-4a0a-afbe-06a2424b6090
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e91e1c7a1586c0b2aff3630bfd8a9a6cd60ef53c
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889572"
---
# <a name="client-architecture-requirements-for-analysis-services-development"></a>Требования к архитектуре клиента для разработки служб Analysis Services
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает архитектурус[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] тонким клиентом. Подсистема [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] вычислений полностью основана на сервере, поэтому все запросы разрешаются на сервере. В результате для каждого запроса требуется только одно перемещение данных от клиента к серверу и обратно, что позволяет масштабировать производительность по мере роста сложности запросов.  
  
 Собственный протокол [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] — это XML для аналитики (XML/A). [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] содержит несколько интерфейсов доступа для клиентских приложений, но все эти компоненты взаимодействуют с экземпляром [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с использованием XML для аналитики.  
  
 В службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] входят несколько различных поставщиков для поддержки различных языков программирования. Поставщик обменивается данными с сервером служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], отправляя и принимая данные XML для аналитики в пакетах SOAP по протоколу TCP/IP или HTTP через службы IIS. HTTP-сеанс использует СОМ-объект, экземпляр которого создается службами IIS и который называется средством переноса данных. Этот объект действует в качестве канала для данных служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Средство переноса данных никак не просматривает базовые данные, которые содержатся в HTTP-потоке, и никакие структуры базовых данных не доступны никакому коду в самой библиотеке данных.  
  
 ![Архитектура логического клиента для Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-clientarch9.gif "Архитектура логического клиента для Analysis Services")  
  
 Клиентские приложения Win32 могут подключаться к серверу служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью интерфейсов OLE DB для OLAP объектной модели Microsoft® ActiveX® (ADO) для языков автоматизации модели СОМ, например Microsoft Visual Basic®. Приложения, написанные на языках платформы .NET, могут подключаться к серверу служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] с помощью ADOMD.NET.  
  
 Существующие приложения могут сообщаться со службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] без изменений, просто используя один из поставщиков служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Язык программирования|Интерфейс доступа к данным|  
|--------------------------|---------------------------|  
|C++|OLE DB для OLAP|  
|Visual Basic 6|ADO MD|  
|Языки платформы .NET|ADO MD.NET|  
|Любой язык с поддержкой SOAP|XML для аналитики|  
  
 Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] отличаются веб-архитектурой с полностью масштабируемым средним уровнем для развертывания как в больших, так и в малых организациях. Службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] предоставляют широкий спектр средств поддержки среднего уровня для веб-служб. Приложения ASP поддерживаются OLE DB для OLAP и объекты данных ActiveX (MD), приложения ASP.NET поддерживаются ADOMD.NET. Средний уровень, проиллюстрированный на приведенном ниже рисунке, масштабируется для одновременной поддержки большого количества пользователей.  
  
 ![Логическая схема для архитектуры среднего уровня](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/as-midtierarch9.gif "Логическая схема для архитектуры среднего уровня")  
  
 И клиентские приложения, и приложения промежуточного уровня могут непосредственно связываться со службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] без использования поставщика. Клиентские приложения и приложения промежуточного уровня могут отправлять данные XML для аналитики в SOAP-пакетах по протоколам TCP/IP, HTTP или HTTPS. Клиент может быть написан на любом языке, поддерживающем SOAP. В этом случае сообщением проще всего управлять посредством служб IIS, используя протокол HTTP, хотя также можно запрограммировать прямое соединение с сервером по протоколу TCP/IP. Это наиболее тонкое из возможных клиентских решений для служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="analysis-services-in-tabular-or-sharepoint-mode"></a>Службы Analysis Services в табличном режиме или режиме интеграции с SharePoint.  
 В [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] сервер может быть запущен в режиме подсистемы VertiPaq аналитики в памяти xVelocity для табличных баз данных и для книг [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)], опубликованных на сайте SharePoint.  
  
 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] — единственные клиентские среды, которые поддерживаются при создании размещенных в памяти баз данных, использующих режим SharePoint или табличный режим соответственно. Внедренная база данных PowerPivot, созданная с помощью Excel и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] средств, содержится в книге Excel и сохраняется как часть файла Excel. xlsx.  
  
 Однако в книге [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] могут использоваться данные, которые хранятся в традиционном кубе, если данные куба импортированы в книгу. Кроме того, можно импортировать данные из другой книги [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)], если она была опубликована на сайте SharePoint.  
  
> [!NOTE]  
>  При использовании куба в качестве источника данных для книги [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] получаемые из куба данные определяются как запрос многомерного выражения, но при этом данные импортируются как плоский моментальный снимок. Нельзя ни работать с данными в интерактивном режиме, ни обновлять их из куба.  
  
### <a name="interfaces-for-powerpivot-client"></a>Интерфейсы для клиента PowerPivot  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]взаимодействует с подсистемой хранилища подсистемы аналитики в памяти xVelocity (VertiPaq) в книге, используя установленные интерфейсы и языки для Analysis Services: Объекты AMO и ADOMD.NET, многомерные выражения и XMLA. В надстройке меры определяются с помощью языка формул, аналогичного языку формул Excel и DAX (выражения анализа данных). Выражения анализа данных внедряются в сообщения XMLA, отправляемые внутрипроцессному серверу.  
  
### <a name="providers"></a>Поставщики  
 При обмене данными между [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и Excel используется поставщик MSOLAP OLEDB (версия 11,0). В поставщике MSOLAP имеется четыре модуля (также называемых транспортами), которые можно использовать для пересылки сообщений между клиентом и сервером.  
  
 **протокол TCP/IP** Используется для обычных подключений "клиент-сервер".  
  
 **Протокол HTTP** Используется для HTTP-соединений через службу обработки данных SSAS или путем вызова компонента SharePoint Web Service (WS).  
  
 **INPROC** Используется для соединений с внутрипроцессный подсистемой.  
  
 **Канал** связи Зарезервировано для обмена данными с системная служба PowerPivot в ферме SharePoint.  
  
## <a name="see-also"></a>См. также  
 [Серверные компоненты ядра OLAP](olap-engine-server-components.md)  
  
  
