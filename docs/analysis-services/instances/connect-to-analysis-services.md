---
title: Подключитесь к службам Analysis Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a7874a45b8cd11ed288448ff025b6c3918251539
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-analysis-services"></a>Подключение к службам Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В этом разделе содержатся сведения о свойствах строки подключения, клиентских библиотеках, используемых для подключений, методах проверки подлинности, поддерживаемых службами Analysis Services, настройке и отмене подключений перед переводом сервера в автономный режим.  

Дополнительные сведения о подключении к службам Analysis Services Azure см. в разделе [соединение с сервером](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect).
  
## <a name="analysis-services-connections"></a>Подключение к службами Analysis Services  
 В службах Analysis Services в качестве протокола связи используется сетевой протокол TCP и XML для аналитики (XMLA). На самом низком уровне все клиентские библиотеки, предоставленные с помощью служб Analysis Services, реализуют схему связи "XMLA по TCP". Несмотря на возможность создания приложений на основе необработанного кода XMLA, большинство приложений и разработчиков приложений задействуют библиотеки, чтобы использовать преимущества объектных моделей и кода. Для клиентских подключений к службам Analysis Services можно использовать IIS как промежуточное подключение, если не удается использовать TCP через стек. Одно из преимуществ использования доступа по протоколу HTTP через IIS — возможность подключения из приложений, которые передают учетные данные в строке подключения.  
  
 Если речь идет о подключении, неизбежно рассматривается проверка подлинности. В отличие от других компонентов SQL Server, службы Analysis Services поддерживают только учетные данные Windows. В серверном подключении к службам Analysis Services нельзя использовать проверку подлинности базы данных SQL Server, проверку подлинности утверждений, проверку подлинности на основе форм или дайджест. Подробные сведения о проверке подлинности приведены в этом разделе.  
  
##  <a name="bkmk_clientApps"></a> Задачи подключения  
  
|Ссылка|Описание задачи|  
|----------|----------------------|  
|[Подключение из клиентских приложений & #40; Службы Analysis Services & #41;](../../analysis-services/instances/connect-from-client-applications-analysis-services.md)|Пользователи, не имеющие опыта работы со службами Analysis Services, должны прочитать этот раздел, прежде чем приступать к работе со средствами и приложениями, которые наиболее часто используются со службами Analysis Services.|  
|[Свойства строки соединения & #40; Службы Analysis Services & #41;](../../analysis-services/instances/connection-string-properties-analysis-services.md)|Службы Analysis Services включают множество свойств сервера и базы данных, позволяющих настроить соединение для конкретного приложения, независимо от настройки экземпляра или базы данных.|  
|[Методики проверки подлинности, поддерживаемые службами Analysis Services](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)|Этот раздел представляет собой краткое введение в методы проверки подлинности, используемые службами Analysis services.|  
|[Настройка служб Analysis Services для ограниченного делегирования Kerberos](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md)|Для многих решений бизнес-аналитики требуется олицетворение, чтобы гарантировать, что каждый пользователь получает только разрешенные данные. В этом разделе рассматриваются требования для использования олицетворения. В этом разделе также приводится описание действий по настройке служб Analysis Services для ограниченного делегирования Kerberos.|  
|[Регистрация имени участника-службы для экземпляра служб Analysis Services](../../analysis-services/instances/spn-registration-for-an-analysis-services-instance.md)|Для проверки подлинности Kerberos требуется имя участника-службы, которая олицетворяет или делегирует удостоверения пользователя в многосерверных решениях. Сведения в этом разделе позволяют получить представление о разработке и шагах для регистрации имени участника-службы для служб Analysis Services.|  
|[Настройка HTTP-доступа к службам Analysis Services в службах IIS & #40; IIS & #41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|Обычная проверка подлинности и кросс-доменные границы — две веские причины для настройки служб Analysis Services для доступа по протоколу HTTP.|  
|[Поставщики данных, используемые для соединений служб Analysis Services](../../analysis-services/instances/data-providers-used-for-analysis-services-connections.md)|Службы Analysis Services предоставляют три клиентские библиотеки для доступа к операциям на сервере или данным служб Analysis Services. Этот раздел содержит краткое введение в ADOMD.NET, службы Analysis Services (AMO) и работу поставщика OLE DB для служб Analysis Services (MSOLAP).|  
|[Отключение пользователей и сеансов на сервер служб Analysis Services](../../analysis-services/instances/disconnect-users-and-sessions-on-analysis-services-server.md)|Сбросьте существующие сеансы и соединения, прежде чем переводить сервер в режим «вне сети» или выполнять базовые тесты производительности.|  
  
## <a name="see-also"></a>См. также  
 [После установки конфигурации & #40; Службы Analysis Services & #41;](../../analysis-services/instances/post-install-configuration-analysis-services.md)   
 [Свойства сервера служб Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
  
  
