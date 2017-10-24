---
title: "Разработка с помощью API REST для служб Reporting Services | Документы Microsoft"
ms.description: The REST API provides programmatic access to the objects in a SQL Server 2017 Reporting Services report server catalog.
ms.date: 10/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 7c2c34047ac316045387b036cf10ee149175580a
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="develop-with-the-rest-apis-for-reporting-services"></a>Разработка с помощью API REST для служб Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

Службы отчетов Microsoft SQL Server 2017 г. поддерживает Representational State Transfer (REST) API-интерфейсы. Интерфейсы API REST, создание конечных точек, которые поддерживают набор операций HTTP (методы), которые предоставляют службы, получения, обновления или удаления доступа для ресурсов в сервере отчетов.

REST API обеспечивает программный доступ к объектам в каталог сервера отчетов служб отчетов SQL Server 2017 г. Примерами объектов являются папки, отчеты, ключевые показатели эффективности, источники данных, наборы данных, планы обновления, подписки и многое другое. С помощью REST API, можно, например, перемещение по иерархии папок, обнаружение содержимое папки или загрузить определение отчета. Можно также создать, обновить и удалить объекты. Примеры работы с объектами передать отчет, выполните план обновления, удаления папки и так далее.

## <a name="components-of-a-rest-api-requestresponse"></a>Компоненты API-интерфейса REST запрос ответ

Пара запросов и ответов REST API можно разделить на пять компонентов:

* **URI запроса**, который состоит из: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Несмотря на то, что URI запроса включается в заголовке сообщения запроса, мы указывают его отдельно, так как большинство языков или платформ требуется передать его отдельно из сообщения запроса.

    * Схема URI: Указывает протокол, используемый для передачи запроса. Например `http` или `https`.
    * URI узла: Указывает имя или IP-адрес сервера, конечная точка REST службы размещения, таких как `myserver.contoso.com`.
    * Путь к ресурсу: задает коллекцию ресурсов, которые могут содержать несколько сегментов, используемых службой в определение выделения этих ресурсов или ресурсов. Например: `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` может использоваться для получения CatalogItem указанных свойств.
    * (Необязательно) строка запроса: предоставляет дополнительные простые параметры, такие как критерий выбора для API версии или ресурсов.

* Поля заголовка сообщения HTTP запроса:

    * Обязательный [метод HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (также известный как результат операции или команду), который сообщает службе типа операции, для которого запрашивается. Reporting API REST служб поддержки DELETE, GET, HEAD, PUT, POST и применить обновления методы.
    * Необязательные дополнительные поля заголовка, требуемые для указанного URI и HTTP-метода.

* Необязательный HTTP **текст сообщения запроса** поля для поддержки операции URI и HTTP. Например операции POST содержать MIME-закодированном объектов, которые передаются как параметры сложных. Для операций POST или PUT, кодирование MIME тип тела должно быть указано в `Content-type` также заголовок запроса. Некоторые службы требуется использование конкретного типа MIME, например `application/json`.

* HTTP **заголовка ответного сообщения** поля:

    * [Код состояния HTTP](http://www.w3.org/Protocols/HTTP/HTRESP.html)— от кодов успешного выполнения 2xx до 4xx или 5xx коды ошибок. Кроме того код состояния, определенные службы могут быть возвращены, как указано в документации по API.
    * Необязательные дополнительные поля заголовка, как требуется для поддержки запроса-ответа, такие как `Content-type` заголовок ответа.

* Необязательный HTTP **тело сообщения ответа** поля:

    * MIME-закодированном ответа объекты возвращаются в тексте ответа HTTP, такие как ответа от метода GET, который возвращает данные. Как правило, эти объекты возвращаются в структурированном виде, например JSON или XML, как указано в `Content-type` заголовок ответа.

## <a name="api-documentation"></a>Документация по API

Современные API REST вызывает для современной документации API. API-Интерфейс REST основана на спецификации OpenAPI (так) Спецификация swagger) и документация доступна на [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0). За Документирование API, SwaggerHub помогает сформировать клиентской библиотеки на языке возможность выбора, JavaScript, TypeScript, C#, Java, Python, Ruby и многое другое.

## <a name="testing-api-calls"></a>Тестирование вызовы API

— Это средство тестирования сообщения запросов и ответов HTTP [Fiddler](http://www.telerik.com/fiddler). Fiddler — это бесплатные веб-, прокси-сервером отладки, может перехватить запросов REST, что упрощает диагностику HTTP-запроса и сообщений-ответов.

## <a name="next-steps"></a>Следующие шаги

Просмотрите доступные интерфейсы API через на [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0).

Образцы доступны на [GitHub](https://github.com/Microsoft/Reporting-Services). Образец включает HTML5 приложения, созданного на TypeScript, webpack, а также пример PowerShell и реагирование на них.

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
