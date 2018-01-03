---
title: "Поставщик Microsoft OLE DB для публикации в Интернете | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 81b34a20948dc53bb16bdd2c9442895af711adb2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Поставщик Microsoft OLE DB для Общие сведения о публикации в Интернете
Поставщик Microsoft OLE DB для публикаций в Интернете позволяет ADO для доступа к ресурсам, обслуживаемых Microsoft FrontPage или Microsoft Internet Information Server. Ресурсы включают web исходные файлы, например HTML-файлы или веб-папок Windows 2000.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
MSDAIPP.DSO
```

 Это значение можно также задать или прочитать с помощью [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 -или-

```
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Description|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для публикации в Интернете.|
|**Источник данных** - или - **URL-адрес**|Указывает URL-адрес к файлу или каталогу, опубликованных в веб-папке.|
|**Идентификатор пользователя**|Указывает имя пользователя.|
|**Пароль**|Указывает пароль пользователя.|

> [!NOTE]
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

 Если задать *ResourceURL* значение из «URL-адрес =» в строке подключения имеет недопустимое значение по умолчанию службу публикации в Интернете вызывает диалоговое окно запрашивает допустимое значение. Это нежелательное поведение компонента на среднем уровне приложения, так как он приостанавливает выполнение программы до диалоговым окном очищается, и клиент, по-видимому, закрепление, так как не получил ответ от компонента.

> [!NOTE]
>  Если MSDAIPP. Объекты DSO явно указано в качестве значения поставщика, с помощью *поставщика* ключевое слово строки подключения или **поставщика** свойство, нельзя использовать «URL-адрес =» в строке подключения. В противном случае возникнет ошибка. Вместо этого просто укажите URL-адрес как показано в разделе [с помощью ADO с поставщиком OLE DB для публикаций в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md).

## <a name="see-also"></a>См. также:
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md) [поставщика OLE DB для публикации в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)
