---
title: Свойство ActiveConnection (ADO MD) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c030a9c1106338975a799a6057bd3eb876b5aa72
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283203"
---
# <a name="activeconnection-property-ado-md"></a>Свойство ActiveConnection (ADO MD)
Указывает, какие ADO [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта текущего набора ячеек или каталога в данный момент принадлежит.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Variant** , содержащий строку, определяющую соединение или **подключения** объекта. Значение по умолчанию является пустым.  
  
## <a name="remarks"></a>Примечания  
 Это свойство может быть присвоено допустимое ADO **подключения** объекта или допустимую строку соединения. Если это свойство имеет значение в строку соединения, поставщик создает новую **подключение** с помощью данного определения и открывает соединение.  
  
 При использовании *ActiveConnection* аргумент [откройте](../../../ado/reference/ado-md-api/open-method-ado-md.md) метод, чтобы открыть [ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта, **ActiveConnection** свойство наследовать значения аргумента.  
  
 Установка **ActiveConnection** свойство [каталога](../../../ado/reference/ado-md-api/catalog-object-ado-md.md) объект **ничего** освобождает связанные данные, включая данные в [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) коллекции и любые связанные [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md), и [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объектов. Закрытие **подключения** объекта, использовавшегося для открытия **каталога** действует так же, как параметр **ActiveConnection** свойства **ничего**.  
  
 Изменение базы данных по умолчанию соединения ссылается **ActiveConnection** свойство **каталога** объекта делает недействительным содержимое **каталога**.  
  
 Произойдет ошибка при попытке изменить **ActiveConnection** свойство для открытого **ячеек** объекта.  
  
> [!NOTE]
>  В Visual Basic, не забывайте использовать **задать** ключевое слово, при задании **ActiveConnection** свойства **подключения** объекта. Если не указан **задать** ключевое слово, то будет фактически путем установки **ActiveConnection** значения свойства **подключения** свойство объекта по умолчанию,  **ConnectionString**. Этот код будет работать; Тем не менее вы создадите дополнительного соединения с источником данных, который может иметь негативное влияние.  
  
 При использовании поставщика данных MSOLAP, задать источник данных в строке подключения имени сервера и установить исходного каталога имя каталога из источника данных. Для подключения к файлу куба, которая отсоединена от сервера, задайте местоположение полный путь. Файл, КУБ. В любом случае установите поставщик для имени поставщика. Например, следующая строка использует поставщик MSOLAP для подключения к каталогу, с именем Bobs видео хранилища на сервере с именем **Servername**:  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 Следующая строка подключается к локальному файлу куба в расположении C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub:  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект Catalog (многомерные объекты ADO)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Объект Cellset (многомерные объекты ADO)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|  
  
## <a name="see-also"></a>См. также  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Метод Open (многомерные объекты ADO)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
