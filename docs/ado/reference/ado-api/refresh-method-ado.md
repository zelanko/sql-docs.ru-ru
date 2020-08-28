---
description: Метод Refresh (ADO)
title: Метод Refresh (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 66324860f931a919cccc36d3de9464d2ad2e48d0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989615"
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
 Использование метода **Refresh** в коллекции [Parameters](./parameters-collection-ado.md) объекта [Command](./command-object-ado.md) возвращает сведения о параметрах на стороне поставщика для хранимой процедуры или параметризованного запроса, указанного в объекте **Command** . Коллекция будет пустой для поставщиков, которые не поддерживают вызовы хранимых процедур или параметризованные запросы.  
  
 Необходимо задать для свойства [ActiveConnection](./activeconnection-property-ado.md) объекта **Command** допустимый объект [соединения](./connection-object-ado.md) , свойство [CommandText](./commandtext-property-ado.md) — допустимую команду, а свойство [CommandType](./commandtype-property-ado.md) — значение **адкмдсторедпрок** перед вызовом метода **Refresh** .  
  
 Если вы обращаетесь к коллекции **Parameters** перед вызовом метода **Refresh** , то ADO автоматически вызывает метод и заполняет коллекцию.  
  
> [!NOTE]
>  Если вы используете метод **Refresh** для получения сведений о параметрах от поставщика и возвращает один или несколько объектов [параметров](./parameter-object.md) типа данных переменной длины, ADO может выделить память для параметров на основе максимального возможного размера, что приведет к ошибке во время выполнения. Необходимо явно задать свойство [size](./size-property-ado-parameter.md) для этих параметров перед вызовом метода [EXECUTE](./execute-method-ado-command.md) для предотвращения ошибок.  
  
### <a name="fields"></a>Поля  
 Использование метода **Refresh** в коллекции [Fields](./fields-collection-ado.md) не имеет видимого результата. Чтобы получить изменения из базовой структуры базы данных, необходимо использовать либо метод [Requery](./requery-method.md) , либо, если объект [набора записей](./recordset-object-ado.md) не поддерживает закладки, метод [MoveFirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) .  
  
### <a name="properties"></a>Свойства  
 Использование метода **Refresh** в коллекции **свойств** некоторых объектов заполняет коллекцию динамическими свойствами, предоставляемыми поставщиком. Эти свойства предоставляют сведения о функциональных возможностях, характерных для поставщика, помимо встроенных свойств, поддерживаемых ADO.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Коллекция осей](../ado-md-api/axes-collection-ado-md.md)  
        [Коллекция Columns](../adox-api/columns-collection-adox.md)  
        [Коллекция Кубедефс](../ado-md-api/cubedefs-collection-ado-md.md)  
        [Коллекция Dimensions](../ado-md-api/dimensions-collection-ado-md.md)  
        [Коллекция ошибок](./errors-collection-ado.md)  
        [Коллекция Fields](./fields-collection-ado.md)  
        [Коллекция Groups](../adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Коллекция иерархий](../ado-md-api/hierarchies-collection-ado-md.md)  
        [Коллекция indexes](../adox-api/indexes-collection-adox.md)  
        [Коллекция Keys](../adox-api/keys-collection-adox.md)  
        [Коллекция Levels](../ado-md-api/levels-collection-ado-md.md)  
        [Коллекция members](../ado-md-api/members-collection-ado-md.md)  
        [Коллекция Parameters](./parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Коллекция Positions](../ado-md-api/positions-collection-ado-md.md)  
        [Коллекция процедур](../adox-api/procedures-collection-adox.md)  
        [Коллекция Properties](./properties-collection-ado.md)  
        [Коллекция таблиц](../adox-api/tables-collection-adox.md)  
        [Коллекция пользователей](../adox-api/users-collection-adox.md)  
        [Коллекция представлений](../adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример метода Refresh (Visual Basic)](./refresh-method-example-vb.md)   
 [Пример метода Refresh (Visual c++)](./refresh-method-example-vc.md)   
 [Свойство Count (ADO)](./count-property-ado.md)   
 [Метод Refresh (служба удаленных рабочих столов)](../rds-api/refresh-method-rds.md)