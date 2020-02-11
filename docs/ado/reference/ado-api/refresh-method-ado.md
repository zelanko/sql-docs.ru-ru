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
ms.openlocfilehash: a676bf5eb3d8d98f1b2eb9367aa8ad56f0da209d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931252"
---
# <a name="refresh-method-ado"></a>Метод Refresh (ADO)
Обновляет объекты в коллекции, чтобы отразить объекты, доступные в поставщике, и связанные с ним.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Remarks  
 Метод **Refresh** выполняет различные задачи в зависимости от коллекции, из которой он вызывается.  
  
### <a name="parameters"></a>Параметры  
 Использование метода **Refresh** в коллекции [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) объекта [Command](../../../ado/reference/ado-api/command-object-ado.md) возвращает сведения о параметрах на стороне поставщика для хранимой процедуры или параметризованного запроса, указанного в объекте **Command** . Коллекция будет пустой для поставщиков, которые не поддерживают вызовы хранимых процедур или параметризованные запросы.  
  
 Необходимо задать для свойства [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) объекта **Command** допустимый объект [соединения](../../../ado/reference/ado-api/connection-object-ado.md) , свойство [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) — допустимую команду, а свойство [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) — значение **адкмдсторедпрок** перед вызовом метода **Refresh** .  
  
 Если вы обращаетесь к коллекции **Parameters** перед вызовом метода **Refresh** , то ADO автоматически вызывает метод и заполняет коллекцию.  
  
> [!NOTE]
>  Если вы используете метод **Refresh** для получения сведений о параметрах от поставщика и возвращает один или несколько объектов [параметров](../../../ado/reference/ado-api/parameter-object.md) типа данных переменной длины, ADO может выделить память для параметров на основе максимального возможного размера, что приведет к ошибке во время выполнения. Необходимо явно задать свойство [size](../../../ado/reference/ado-api/size-property-ado-parameter.md) для этих параметров перед вызовом метода [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md) для предотвращения ошибок.  
  
### <a name="fields"></a>Поля  
 Использование метода **Refresh** в коллекции [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) не имеет видимого результата. Чтобы получить изменения из базовой структуры базы данных, необходимо использовать либо метод [Requery](../../../ado/reference/ado-api/requery-method.md) , либо, если объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) не поддерживает закладки, метод [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) .  
  
### <a name="properties"></a>Свойства  
 Использование метода **Refresh** в коллекции **свойств** некоторых объектов заполняет коллекцию динамическими свойствами, предоставляемыми поставщиком. Эти свойства предоставляют сведения о функциональных возможностях, характерных для поставщика, помимо встроенных свойств, поддерживаемых ADO.  
  
## <a name="applies-to"></a>Применяется к  
  
||||  
|-|-|-|  
|[Коллекция осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Коллекция Columns](../../../ado/reference/adox-api/columns-collection-adox.md)|[Коллекция Кубедефс](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Коллекция Dimensions](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Коллекция ошибок](../../../ado/reference/ado-api/errors-collection-ado.md)|[Коллекция Fields](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Коллекция Groups](../../../ado/reference/adox-api/groups-collection-adox.md)|[Коллекция иерархий](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Коллекция indexes](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Коллекция Keys](../../../ado/reference/adox-api/keys-collection-adox.md)|[Коллекция Levels](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Коллекция members](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Коллекция Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Коллекция Positions](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Коллекция процедур](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Коллекция Properties](../../../ado/reference/ado-api/properties-collection-ado.md)|[Коллекция таблиц](../../../ado/reference/adox-api/tables-collection-adox.md)|[Коллекция пользователей](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Коллекция представлений](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Refresh (Visual Basic)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Пример метода Refresh (Visual c++)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Свойство Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Метод Refresh (служба удаленных рабочих столов)](../../../ado/reference/rds-api/refresh-method-rds.md)
