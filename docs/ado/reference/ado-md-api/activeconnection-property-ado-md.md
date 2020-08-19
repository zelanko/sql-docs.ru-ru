---
description: Свойство ActiveConnection (многомерные объекты ADO)
title: Свойство ActiveConnection (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f226f9687f1bce3def616739f43f4d283d019ea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441446"
---
# <a name="activeconnection-property-ado-md"></a>Свойство ActiveConnection (многомерные объекты ADO)
Указывает объект [подключения](../../../ado/reference/ado-api/connection-object-ado.md) ADO, к которому в настоящий момент принадлежит текущий набор ячеек или каталог.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **значение типа Variant** , содержащее строку, определяющую соединение или объект **соединения** . Значение по умолчанию — Empty.  
  
## <a name="remarks"></a>Remarks  
 Этому свойству можно присвоить допустимый объект **соединения** ADO или допустимую строку подключения. Если для этого свойства задана строка подключения, поставщик создает новый объект **соединения** , используя это определение, и открывает соединение.  
  
 При использовании аргумента *ActiveConnection* метода [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) для открытия объекта набора [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) свойство **ActiveConnection** будет наследовать значение аргумента.  
  
 Присвоение свойству **ActiveConnection** объекта [каталога](../../../ado/reference/ado-md-api/catalog-object-ado-md.md) значения **Nothing** приведет к освобождению связанных данных, включая данные из коллекции [кубедефс](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) и любых связанных [объектов измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md)и [элемента](../../../ado/reference/ado-md-api/member-object-ado-md.md) . Закрытие объекта **соединения** , который использовался для открытия **каталога** , имеет тот же результат, что и присвоение свойству **ActiveConnection** значения **Nothing**.  
  
 Изменение базы данных по умолчанию для соединения, на которое ссылается свойство **ActiveConnection** объекта **каталога** , делает недействительным содержимое **каталога**.  
  
 При попытке изменить свойство **ActiveConnection** для открытого объекта набора **ячеек** возникнет ошибка.  
  
> [!NOTE]
>  В Visual Basic не забывайте использовать ключевое слово **Set** при задании свойства **ActiveConnection** для объекта **соединения** . Если опустить ключевое слово **Set** , то будет задано свойство **ActiveConnection** , равное свойству по умолчанию объекта **соединения** , **ConnectionString**. Код будет работать; Однако будет создано дополнительное подключение к источнику данных, что может отрицательно сказаться на производительности.  
  
 При использовании поставщика данных MSOLAP присвойте источнику данных в строке подключения имя сервера и присвойте начальному каталогу имя каталога из источника данных. Чтобы подключиться к файлу куба, отключенному от сервера, задайте в качестве расположения полный путь к. Файл CUB. В любом случае задайте поставщику имя поставщика. Например, следующая строка использует поставщик MSOLAP для подключения к каталогу с именем bobs Video Store на сервере с именем **ServerName**:  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 Следующая строка подключается к локальному файлу куба в расположении К:\мсдасдк\самплес\оледб\олап\дата\бобсвид.куб:  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Catalog (многомерные объекты ADO)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также:  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Метод Open (многомерные объекты ADO)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
