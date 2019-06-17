---
title: Метод Refresh (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0fee14a397104f8320fc01ce29f8364384151922
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711712"
---
# <a name="refresh-method-ado"></a>Метод Refresh (ADO)
Обновляет объекты из коллекции объектов, доступных из, а также конкретных к поставщику.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Примечания  
 **Обновить** метод выполняет различные задачи в зависимости от коллекции, из которого можно вызывать его.  
  
### <a name="parameters"></a>Параметры  
 С помощью **обновить** метод [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекцию [команда](../../../ado/reference/ado-api/command-object-ado.md) извлекает сведения о параметрах на стороне поставщика для хранимой процедуры или параметризованный запрос, указанный в **команда** объекта. Коллекция будет пустой, для поставщиков, которые не поддерживают вызовы хранимой процедуры или параметризованные запросы.  
  
 Необходимо задать [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) свойство **команда** объекта на допустимый [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство Чтобы допустимой команды и [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) свойства **adCmdStoredProc** перед вызовом **обновить** метод.  
  
 При доступе к **параметры** коллекции перед вызовом **обновить** автоматически метод ADO вызовите метод и заполнения коллекции для вас.  
  
> [!NOTE]
>  Если вы используете **обновить** метод, чтобы получить сведения о параметрах от поставщика и он возвращает тип данных переменной длины, один или несколько [параметр](../../../ado/reference/ado-api/parameter-object.md) объектов ADO может выделить память для параметров, на основе на их максимальный потенциальный размер, который приведет к ошибке во время выполнения. Необходимо явно указать [размер](../../../ado/reference/ado-api/size-property-ado-parameter.md) свойства для этих параметров перед вызовом [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод, чтобы избежать ошибок.  
  
### <a name="fields"></a>Поля  
 С помощью **обновить** метод [поля](../../../ado/reference/ado-api/fields-collection-ado.md) коллекции не имеет видимого эффекта. Чтобы получить изменения из базовой структуры базы данных, необходимо использовать [Requery](../../../ado/reference/ado-api/requery-method.md) метода или, если [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект не поддерживает закладки, [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)метод.  
  
### <a name="properties"></a>Свойства  
 С помощью **обновить** метод **свойства** коллекции некоторых объектов заполняет коллекцию динамические свойства, которые предоставляет поставщик. Эти свойства предоставляют сведения о конкретных функциях поставщику, помимо поддерживает встроенные свойства ADO.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Коллекция axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Коллекция столбцов](../../../ado/reference/adox-api/columns-collection-adox.md)|[Коллекция CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Коллекция Dimensions](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Коллекция ошибок](../../../ado/reference/ado-api/errors-collection-ado.md)|[Коллекция полей](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Коллекция групп](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция hierarchies](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Коллекция индексов](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция Keys](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция Levels](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Элементы коллекции](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Коллекция параметров](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Коллекции Positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Коллекция Procedures](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Свойства коллекции](../../../ado/reference/ado-api/properties-collection-ado.md)|[Коллекция Tables](../../../ado/reference/adox-api/tables-collection-adox.md)|[Коллекция пользователей](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Коллекция Views](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>См. также  
 [Метод пример Refresh (Visual Basic)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Обновить пример метода (Visual C++)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Метод Refresh (служба удаленных рабочих столов)](../../../ado/reference/rds-api/refresh-method-rds.md)
