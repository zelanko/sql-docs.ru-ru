---
title: "Поставщик Microsoft OLE DB для Oracle | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], OLE DB provider for Oracle
- OLE DB provider for Oracle [ADO]
- Oracle provider [ADO]
ms.assetid: 44fae9dd-5585-4cd6-8bbd-3248a78931b4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 35bd07e150d1d56a1ea94542b0bd5b3c1b46d3d4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-ole-db-provider-for-oracle-overview"></a>Поставщик Microsoft OLE DB для Oracle Обзор
> [!IMPORTANT]
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте поставщик OLE DB для Oracle.

 Поставщик Microsoft OLE DB для Oracle позволяет ADO для доступа к базам данных Oracle.

## <a name="connection-string-parameters"></a>Параметры строки соединения
 Чтобы подключиться к этому поставщику, задайте *поставщика* аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойства:

```
MSDAORA
```

 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также этой строки.

 Запрос соединения с набором ключей или динамического курсора при выполнении в базе данных Oracle, возникает ошибка. Oracle поддерживает только статический курсор только для чтения.

## <a name="typical-connection-string"></a>Обычная строка соединения
 — Строка соединения для данного поставщика:

```
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
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.

## <a name="provider-specific-connection-parameters"></a>Параметры подключения для конкретного поставщика
 Поставщик поддерживает несколько параметров подключения к конкретному поставщику помимо параметрами, определенными ADO. Как с помощью свойства соединения ADO, эти свойства от поставщика может быть задано посредством [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) или как часть **ConnectionString**.

 Эти параметры являются полностью описаны в [Справочник программиста OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8). [Индекс динамические свойства ADO](../../../ado/reference/ado-api/ado-dynamic-property-index.md) предоставляет перекрестной ссылки между эти имена параметров и соответствующие свойства OLE DB.

|Параметр|Описание|
|---------------|-----------------|
|**Дескриптор окна**|Указывает дескриптор окна для использования для запроса дополнительных сведений.|
|**Идентификатор локали**|Указывает уникальный 32-разрядное число (например, 1033), указывающее параметры, связанные с языком пользователя. Эти параметры указывают способ форматирования даты и времени, элементы сортируются в алфавитном порядке, строки сравниваются и так далее.|
|**Службы OLE DB**|Указывает битовую маску, которая указывает службы OLE DB, чтобы включить или отключить.|
|**Prompt**|Указывает, следует ли запрашивать пользователя во время установления соединения.|
|**Расширенные свойства**|Строка, содержащая поставщика, расширенные сведения о соединении. Это свойство используется только для подключения к конкретному поставщику данных, которые не может быть описан через механизм свойства.|

## <a name="see-also"></a>См. также
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [свойство поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
