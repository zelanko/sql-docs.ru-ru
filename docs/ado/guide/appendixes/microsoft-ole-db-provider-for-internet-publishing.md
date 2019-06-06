---
title: Поставщик Microsoft OLE DB для публикации в Интернете | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 48c6e95a644c643721a7cb1c6f15c5eaf1e5a995
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701393"
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Поставщик Microsoft OLE DB для Общие сведения о публикации в Интернете
Поставщик Microsoft OLE DB для публикаций в Интернете позволяет ADO для доступа к ресурсам, обслуживаемых Microsoft FrontPage или Microsoft Internet Information Server. Ресурсы включают web исходных файлов, например HTML-файлы или веб-папки Windows 2000.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этим поставщиком, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```vb
MSDAIPP.DSO
```

 Это значение можно также задать или прочитать с помощью [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство.

## <a name="typical-connection-string"></a>Типичная строка подключения
 — Строка соединения для данного поставщика:

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
|**Источник данных** - или - **URL-адрес**|Указывает URL-адрес файла или каталога, опубликованной в веб-папки.|
|**Идентификатор пользователя**|Указывает имя пользователя.|
|**Пароль**|Указывает пароль пользователя.|

> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

 Если задать *ResourceURL* значение «URL-адрес =» в строке подключения имеет недопустимое значение по умолчанию службу публикации в Интернете вызывает диалоговое окно запрашивать допустимое значение. Это нежелательное поведение для компонента на среднем уровне приложения, так как он приостанавливает выполнение программы, пока не снят диалоговое окно и клиент, по-видимому, заморозить, так как не получил ответ от компонента.

> [!NOTE]
>  Если MSDAIPP. Объекты DSO явно задается как значение поставщика, с помощью *поставщика* ключевое слово строки подключения или **поставщика** свойство, нельзя использовать «URL-адрес =» в строке подключения. В противном случае произойдет ошибка. Вместо этого просто укажите URL-адрес как показано в разделе [использование объектов ADO с поставщиком OLE DB для публикаций в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md).

## <a name="see-also"></a>См. также
 [Сценарий публикации в Интернете](../../../ado/guide/data/internet-publishing-scenario.md) [поставщика OLE DB для публикации в Интернете](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)
