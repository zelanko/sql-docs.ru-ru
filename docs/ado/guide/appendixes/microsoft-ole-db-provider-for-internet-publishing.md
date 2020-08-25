---
description: Обзор поставщика услуг Microsoft OLE DB для публикации в Интернете
title: Поставщик OLE DB Майкрософт для публикации в Интернете | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
author: rothja
ms.author: jroth
ms.openlocfilehash: 3888cf881fd1b6cdb0ccc2c5985fe4a6e08ae581
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806583"
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Обзор поставщика услуг Microsoft OLE DB для публикации в Интернете
Поставщик Microsoft OLE DB для публикации в Интернете позволяет ADO получать доступ к ресурсам, обслуживаемым Microsoft FrontPage или Microsoft Internet Information Server. К ресурсам относятся исходные файлы веб-системы, такие как HTML-файлы, или папки Windows 2000.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к поставщику, задайте для аргумента *поставщика* свойства [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) значение:

```vb
MSDAIPP.DSO
```

 Это значение также может быть задано или считано с помощью свойства [provider](../../reference/ado-api/provider-property-ado.md) .

## <a name="typical-connection-string"></a>Типичная строка подключения
 Типичная строка подключения для этого поставщика:

```vb
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 -или-

```vb
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для публикации в Интернете.|
|**Источник данных** или URL- **адрес**|Указывает URL-адрес файла или каталога, опубликованного в веб-папке.|
|**Идентификатор пользователя**|Указывает имя пользователя.|
|**Пароль**|Указывает пароль пользователя.|

> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.

 Если задать значение *ResourceURL* из "URL =" в строке подключения к недопустимому значению, то по умолчанию поставщик публикации в Интернете выдаст диалоговое окно для запроса допустимого значения. Это нежелательное поведение для компонента на среднем уровне приложения, так как оно приостанавливает выполнение программы до тех пор, пока не будет снято диалоговое окно и клиент не получит заморозить, так как он не получил ответ от компонента.

> [!NOTE]
>  Если МСДАИПП. Объекты DSO явно указываются в качестве значения поставщика с помощью ключевого слова строки подключения *поставщика* или свойства **поставщика** . в строке подключения нельзя использовать "URL =". В противном случае возникнет ошибка. Вместо этого просто укажите URL-адрес, как показано в разделе [Использование ADO с поставщиком OLE DB для публикации в Интернете](../data/the-ole-db-provider-for-internet-publishing.md).

## <a name="see-also"></a>См. также
 [Сценарий публикации в Интернете](../data/internet-publishing-scenario.md) [поставщик OLE DB для публикации в Интернете](../data/the-ole-db-provider-for-internet-publishing.md)