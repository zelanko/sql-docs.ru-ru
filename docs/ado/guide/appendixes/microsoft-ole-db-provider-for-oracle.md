---
title: Поставщик Microsoft OLE DB для Oracle | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 596d67527807782ee89043e0b198f0923552db7b
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52390820"
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Поставщик Microsoft OLE DB для Oracle Обзор
> [!IMPORTANT]
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте поставщик OLE DB для Oracle.

 Поставщик Microsoft OLE DB для Oracle позволяет ADO для доступа к базам данных Oracle.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этим поставщиком, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```vb
MSDAORA
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также эту строку.

 Если в базе данных Oracle выполняется запрос соединения с курсор keyset или dynamic, возникает ошибка. Oracle поддерживает только статический курсор только для чтения.

## <a name="typical-connection-string"></a>Типичная строка подключения
 — Строка соединения для данного поставщика:

```vb
"Provider=MSDAORA;Data Source=serverName;User ID=MyUserID; Password=MyPassword;"
```

 Строка состоит из следующих ключевых слов:

|Ключевое слово|Описание|
|-------------|-----------------|
|**Поставщик**|Указывает поставщика OLE DB для Oracle.|
|**Источник данных**|Указывает имя сервера.|
|**Идентификатор пользователя**|Указывает имя пользователя.|
|**Пароль**|Указывает пароль пользователя.|

> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения для поставщика
 Поставщик поддерживает несколько параметров подключения для поставщика, помимо определенные ADO. Как с помощью свойства соединения ADO, эти свойства от поставщика может быть переведена с помощью [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) или как часть **ConnectionString**.

 Эти параметры являются полностью описано в [Справочник программиста OLE DB по](https://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8). [Индекс динамических свойств ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) предоставляет перекрестной ссылки между эти имена параметров и соответствующие свойства OLE DB.

|Параметр|Описание|
|---------------|-----------------|
|**Дескриптор окна**|Указывает дескриптор окна, в которых будет производиться запрашивают дополнительную информацию.|
|**Идентификатор локали**|Указывает уникальный 32-разрядное число (например, 1033), указывающее параметры, связанные с языком пользователя. Эти параметры указывают способ форматирования значения даты и времени, элементы сортируются в алфавитном порядке, строк сравниваются и так далее.|
|**Службы OLE DB**|Указывает, битовая маска, определяющая службы OLE DB, чтобы включить или отключить.|
|**Запрос**|Указывает, следует ли запрашивать пользователя во время установления соединения.|
|**Расширенные свойства**|Строка, содержащая зависящий от поставщика расширенные данные о соединении. Это свойство используется только для подключения к конкретному поставщику данных, которые не может быть описан через механизм свойство.|

## <a name="see-also"></a>См. также
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [свойство Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
