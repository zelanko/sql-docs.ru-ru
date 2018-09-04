---
title: Разработка с помощью API REST для служб Reporting Services | Документы Майкрософт
ms.description: The REST API provides programmatic access to the objects in a SQL Server 2017 Reporting Services report server catalog.
ms.date: 05/25/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: developer
ms.suite: pro-bi
ms.topic: conceptual
author: markingmyname
ms.author: maghan
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 1b2094b632ce71498f2eb9f88d1685e2b667616f
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43271835"
---
# <a name="develop-with-the-rest-apis-for-reporting-services"></a>Разработка с помощью API REST для служб Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

Службы отчетов Microsoft SQL Server 2017 поддерживают API-интерфейсы REST. API-интерфейсы REST — это конечные точки службы, которые поддерживают набор операций HTTP (методов), предоставляющих доступ на создание, получение, обновление или удаление ресурсов в сервере отчетов.

API REST обеспечивает программный доступ к объектам в каталоге сервера отчетов служб SQL Server 2017 Reporting Services. Примерами объектов являются папки, отчеты, ключевые показатели эффективности, источники данных, наборы данных, планы обновления, подписки и многое другое. С помощью API REST можно, например, перемещаться по иерархии папок, обнаруживать содержимое папки или загружать определение отчета. Можно также создавать, обновлять и удалять объекты. Примерами работы с объектами являются отправка отчета, выполнение плана обновления, удаление папки и т. д.

[!INCLUDE [GDPR-related guidance](../../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>Компоненты запроса и ответа API REST

Пару запроса-ответа API REST можно разделить на пять компонентов:

* **URI запроса**, который состоит из: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Несмотря на то, что URI запроса включается в заголовок сообщения запроса, мы выделяем его отдельно, так как большинство языков или платформ требуют передавать его отдельно от сообщения запроса.

    * Схема URI: указывает протокол, используемый для передачи запроса. Например, `http` или `https`.
    * Узел URI: указывает имя домена или IP-адрес сервера, где размещена конечная точка службы REST, например `myserver.contoso.com`.
    * Путь к ресурсу: указывает ресурс или коллекцию ресурсов, которые могут содержать несколько сегментов, используемых службой для определения выборки этих ресурсов. Например: для получения указанных свойств CatalogItem можно использовать `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties`.
    * Строка запроса (необязательно): предоставляет дополнительные простые параметры, такие как критерий выбора ресурса или версии API.

* Поля заголовка сообщения HTTP-запроса:

    * Обязательный [метод HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (также известный как операция или команда), который сообщает службе, какой тип операции запрашивается. API-интерфейсы REST служб Reporting Services поддерживают методы DELETE, GET, HEAD, PUT, POST и PATCH.
    * Необязательные дополнительные поля заголовка, требуемые для указанного URI и метода HTTP.

* Необязательные поля **текста сообщения запроса** HTTP для поддержки URI и операции HTTP. Например, операции POST содержат объекты в кодировке MIME, которые передаются как сложные параметры. Для операций POST или PUT тип в кодировке MIME текста должен быть указан в заголовке запроса `Content-type`. Для некоторых служб необходимо использовать конкретный тип MIME, например `application/json`.

* Поля **заголовка сообщения ответа** HTTP:

    * [Код состояния HTTP](http://www.w3.org/Protocols/HTTP/HTRESP.html)— от кодов успешного выполнения 2xx до кодов ошибок 4xx или 5xx. Кроме того, может быть возвращен определяемый службой код состояния, как указано в документации по API.
    * Необязательные дополнительные поля заголовка, как требуется для поддержки ответа запроса, такие как заголовок ответа `Content-type`.

* Необязательные поля **текста сообщения ответа** HTTP:

    * В тексте ответа HTTP возвращаются объекты ответа в кодировке MIME, например ответ от метода GET, который возвращает данные. Как правило, эти объекты возвращаются в структурированном виде, например JSON или XML, как указано в заголовке ответа `Content-type`.

## <a name="api-documentation"></a>Документирование API

Современный API REST требуется для современного документирования API. API-интерфейс REST основан на спецификации OpenAPI (также известной как спецификация swagger), а соответствующая документация доступна на сайте [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0). Помимо документирования API SwaggerHub помогает создать клиентскую библиотеку на нужном языке — JavaScript, TypeScript, C#, Java, Python, Ruby и т. д.

## <a name="testing-api-calls"></a>Тестирование вызовов API

Для тестирования сообщений запросов и ответов HTTP используется средство [Fiddler](http://www.telerik.com/fiddler). Fiddler — это бесплатный прокси-сервер веб-отладки, который может перехватывать запросы REST, что упрощает диагностику сообщений запросов и ответов HTTP.

## <a name="next-steps"></a>Следующие шаги

Ознакомьтесь с доступными API-интерфейсами на сайте [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0).

Образцы можно найти на сайте [GitHub](https://github.com/Microsoft/Reporting-Services). Образец включает в себя приложение HTML5, созданное на TypeScript, React и webpack с примером PowerShell.

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
