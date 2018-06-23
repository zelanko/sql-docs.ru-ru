---
title: Набор строк схемы MDSCHEMA_ACTIONS | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_ACTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_ACTIONS rowset
ms.assetid: f73081f8-ac51-4286-b46e-2b34e792c3e0
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5b3e3a4c91d998e0ba0459577f1e0b469ec7f78b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192112"
---
# <a name="mdschemaactions-rowset"></a>Набор строк MDSCHEMA_ACTIONS
  Описывает действия, доступные для клиентского приложения.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 `MDSCHEMA_ACTIONS` Набор строк содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Имя базы данных.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Не поддерживается. Всегда содержит `VT_NULL`.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Имя куба, которому принадлежит это действие.|  
|`ACTION_NAME`|`DBTYPE_WSTR`||Имя этого действия.|  
|`ACTION_TYPE`|`DBTYPE_I4`||Битовая карта, которая служит для задания метода срабатывания действия. В файле Msmd.h определены следующие битовые константы для этой битовой карты.<br /><br /> -   `MDACTION_TYPE_URL` (`0x01`)<br />-   `MDACTION_TYPE_HTML` (`0x02`)<br />-   `MDACTION_TYPE_STATEMENT` (`0x04`)<br />-   `MDACTION_TYPE_DATASET` (`0x08`)<br />-   `MDACTION_TYPE_ROWSET` (`0x10`)<br />-   `MDACTION_TYPE_COMMANDLINE` (`0x20`)<br />-   `MDACTION_TYPE_PROPRIETARY` (`0x40`)<br />-   `MDACTION_TYPE_REPORT` (`0x80`)<br />-   `MDACTION_TYPE_DRILLTHROUGH` (`0x100`)|  
|`COORDINATE`|`DBTYPE_WSTR`||Многомерное выражение, указывающее объект или координату в многомерном пространстве, в котором выполняется действие. За передачу значения этого столбца ограничений отвечает клиентское приложение.<br /><br /> Элемент `CORDINATE` должен быть разрешен до объекта, указанного в `COORDINATE_TYPE`.|  
|`COORDINATE_TYPE`|`DBTYPE_I4`||Битовая карта, указывающая способ интерпретации столбца ограничений `COORDINATE`. В файле Msmd.h определены следующие битовые константы для этой битовой карты.<br /><br /> -   `MDACTION_COORDINATE_CUBE` (`1`)<br />-   `MDACTION_COORDINATE_DIMENSION` (`2`)<br />     ссылается на иерархии измерений.<br />-   `MDACTION_COORDINATE_LEVEL` (`3`)<br />-   `MDACTION_COORDINATE_MEMBER` (`4`)<br />-   `MDACTION_COORDINATE_SET` (`5`)<br />-   `MDACTION_COORDINATE_CELL` (`6`)|  
|`ACTION_CAPTION`|`DBTYPE_WSTR`||Имя действия, если заголовок не указан и в DDL не заданы переводы.<br /><br /> Если заголовок или переводы не указаны, а `CaptionIsMDX` имеет значение false, то одна из следующих строк:<br /><br /> -Перевод для соответствующего языка.<br />-Указанный заголовок, если для указанного языка перевод не найден.<br />-Имя действия, если перевод не найден и заголовок не указан в инструкции DDL.<br /><br /> Если заголовок или перевод указаны, а `CaptionIsMDX` имеет значение true, то строка, являющаяся результатом поиска соответствующего перевода для указанного языка или указанного перевода в DDL и вычисления формулы для создания строки.<br /><br /> Если действие задано в скрипте многомерных выражений, то перевод отсутствует, а заголовок всегда рассматривается как многомерное выражение.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Понятное описание действия.|  
|`CONTENT`|`DBTYPE_WSTR`||Выражение или содержимое действия, которое должно быть запущено.|  
|`APPLICATION`|`DBTYPE_WSTR`||Имя приложения, используемого для запуска действия.|  
|`INVOCATION`|`DBTYPE_I4`||Сведения о способе вызова действия.<br /><br /> -   `MDACTION_INVOCATION_INTERACTIVE` (`1`) указывает на регулярное действие, используемые во время обычной работы. Это значение по умолчанию для этого столбца.<br />-   `MDACTION_INVOCATION_ON_OPEN` (`2`) указывает, что действие должно выполняться при первом открытии куба.<br />-   `MDACTION_INVOCATION_BATCH` (`4`) указывает, что действие выполняется как часть пакетной операции или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] задачи.<br /><br /> Эти значения перечисления определены в файле Msmd.h.|  
  
 Набор строк отсортирован по полям `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `ACTION_NAME`.  
  
> [!NOTE]  
>  Для действий типа `MDACTION_TYPE_PROPRIETARY` всегда должно указываться значение для столбца `APPLICATION`.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк `MDSCHEMA_ACTIONS` может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Обязательный|  
|`ACTION_NAME`|`DBTYPE_WSTR`|Необязательно|  
|`ACTION_TYPE`|`DBTYPE_I4`|Необязательно|  
|`COORDINATE`|`DBTYPE_WSTR`|Обязательный|  
|`COORDINATE_TYPE`|`DBTYPE_I4`|Обязательный|  
|`INVOCATION`|`DBTYPE_I4`|Столбец ограничений `INVOCATION` принимает значение по умолчанию `MDACTION_INVOCATION_INTERACTIVE`. Для получения всех действий используйте значение `MDACTION_INVOCATION_ALL` в столбце ограничений `INVOCATION`.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Битовая карта с одним из следующих допустимых значений (необязательно).<br /><br /> -КУБ 1<br />-2 ИЗМЕРЕНИЯ.<br /><br /> Значение по умолчанию для ограничения — 1.|  
  
> [!IMPORTANT]  
>  Столбец ограничений `INVOCATION` имеет значение по умолчанию `MDACTION_INVOCATION_INTERACTIVE`. Набор строк схемы, который не задает явным образом значения для этого столбца, содержит только строки с этим значением. Если набор строк должен содержать весь набор действий, указывайте константу `MDACTION_INVOCATION_ALL` в столбце ограничений `INVOCATION`.  
  
 С помощью оператора OR клиентские приложения могут определить несколько `ACTION_TYPE`.  
  
## <a name="remarks"></a>Примечания  
 В следующей таблице перечислены допустимые сочетания `COORDINATE` и `COORDINATE_TYPE`.  
  
|Тип объекта COORDINATE|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|`Cube`|`MDACTION_COORDINATE_CUBE`|  
|`Dimension`|`MDACTION_COORDINATE_DIMENSION`<br /><br /> `MDACTION_COORDINATE_LEVEL`<br /><br /> `MDACTION_COORDINATE_MEMBER`<br /><br /> `MDACTION_COORDINATE_SET`<br /><br /> `MDACTION_COORDINATE_CELL`|  
|`Hierarchy`|`MDACTION_COORDINATE_DIMENSION`|  
|`Level`|`MDACTION_COORDINATE_LEVEL`|  
|`Member`|`MDACTION_COORDINATE_MEMBER`|  
|`Set`|`MDACTION_COORDINATE_SET`|  
|`cell`|`MDACTION_COORDINATE_CELL`|  
  
## <a name="see-also"></a>См. также  
 [Наборы строк схемы OLE DB для OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  