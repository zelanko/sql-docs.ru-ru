---
title: "Обновить метод (ADO) | Документы Microsoft"
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
apitype: COM
f1_keywords:
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 422f04618e6e63b6143a8459c869316e47450796
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="refresh-method-ado"></a>Обновить метод (ADO)
Обновляет объекты в коллекции объектов, доступных из и относящиеся к поставщику.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Remarks  
 **Обновление** метод выполняет различные задачи в зависимости от коллекции, из которого она вызывается.  
  
### <a name="parameters"></a>Параметры  
 С помощью **обновление** метод [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) извлекает сведения о параметрах на стороне поставщика для хранимой процедуры или параметризованный запрос, указанный в **команда** объекта. Коллекция будет пустой, для поставщиков, которые не поддерживают вызовы хранимой процедуры или параметризованные запросы.  
  
 Необходимо задать [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство **команда** объект является допустимым [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство для допустимой команды и [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) свойства **adCmdStoredProc** перед вызовом **обновление** метод.  
  
 При доступе к **параметры** коллекции перед вызовом **обновление** , метод ADO будет автоматически вызывать метод и заполнения в коллекции.  
  
> [!NOTE]
>  При использовании **обновление** метод, чтобы получить сведения о параметрах от поставщика и он возвращает тип данных переменной длины, один или несколько [параметр](../../../ado/reference/ado-api/parameter-object.md) объекты ADO может выделить память для параметров на основе на их максимальный потенциальный размер, который приведет к ошибке во время выполнения. Необходимо явно задать [размер](../../../ado/reference/ado-api/size-property-ado-parameter.md) свойства для этих параметров перед вызовом [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метода во избежание ошибок.  
  
### <a name="fields"></a>Поля  
 С помощью **обновление** метод [поля](../../../ado/reference/ado-api/fields-collection-ado.md) сбора не имеет видимого эффекта. Чтобы получить изменения из базовой структуры базы данных, необходимо использовать [Requery](../../../ado/reference/ado-api/requery-method.md) метода или, если [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект не поддерживает закладки, [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)метод.  
  
### <a name="properties"></a>Свойства  
 С помощью **обновление** метод **свойства** коллекцию некоторые объекты заполняет коллекцию динамические свойства, которые предоставляет поставщик. Эти свойства предоставляют сведения о функциональные возможности, специфичные для поставщика, помимо поддерживает ADO встроенные свойства.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Коллекция axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Коллекция столбцов](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs коллекции](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Коллекции измерений](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Коллекция ошибок](../../../ado/reference/ado-api/errors-collection-ado.md)|[Коллекция полей](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Коллекция групп](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция hierarchies](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Коллекция индексов](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция ключей](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция уровней](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Элементы коллекции](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Коллекция параметров](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Коллекция позиций](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Коллекция процедур](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Коллекция свойств](../../../ado/reference/ado-api/properties-collection-ado.md)|[Коллекция таблиц](../../../ado/reference/adox-api/tables-collection-adox.md)|[Коллекции пользователей](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Коллекции представлений](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>См. также  
 [Обновить пример метода (Visual Basic)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Обновить пример метода (VC ++)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Метод Refresh (служба удаленных рабочих столов)](../../../ado/reference/rds-api/refresh-method-rds.md)
