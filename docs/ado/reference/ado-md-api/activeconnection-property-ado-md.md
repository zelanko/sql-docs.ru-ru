---
title: Свойство ActiveConnection (многомерные Объекты ADO) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a9ece5a7774ca2b718af90fe041c070fcc99bdb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789383"
---
# <a name="activeconnection-property-ado-md"></a>Свойство ActiveConnection (многомерные объекты ADO)
Указывает, к какой ADO [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта текущего набора ячеек или каталога в настоящее время принадлежит.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Variant** , содержащий строку, определяющую соединение или **подключения** объекта. Значение по умолчанию является пустым.  
  
## <a name="remarks"></a>Примечания  
 Это свойство может быть присвоено допустимое ADO **подключения** объекта или допустимую строку соединения. Если это свойство имеет значение в строку подключения, поставщик создает новую **подключения** с помощью этого определения и открывает соединение.  
  
 При использовании *ActiveConnection* аргумент [откройте](../../../ado/reference/ado-md-api/open-method-ado-md.md) метод, чтобы открыть [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) объекта, **ActiveConnection** будет свойство Наследовать значение аргумента.  
  
 Установка **ActiveConnection** свойство [каталога](../../../ado/reference/ado-md-api/catalog-object-ado-md.md) объект **ничего не** освобождает связанные данные, включая данные в [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) коллекции и все связанные с [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md), и [член](../../../ado/reference/ado-md-api/member-object-ado-md.md) объектов. Закрытие **подключения** объект, который использовался для открытия **каталога** имеет тот же эффект, что параметр **ActiveConnection** свойства **Nothing**.  
  
 Изменение базы данных по умолчанию соединения ссылается **ActiveConnection** свойство **каталога** объекта делает недействительным содержимое **каталога**.  
  
 Произойдет ошибка при попытке изменить **ActiveConnection** свойство для открытого **набора ячеек** объекта.  
  
> [!NOTE]
>  В Visual Basic, не забывайте использовать **задать** ключевое слово при задании **ActiveConnection** свойства **подключения** объекта. Если опустить **задать** ключевое слово, вам будет фактически настраиваться **ActiveConnection** равным **подключения** свойство объекта по умолчанию,  **ConnectionString**. Этот код будет работать; Тем не менее вы создадите дополнительное подключение к источнику данных, который может иметь негативное влияние.  
  
 При использовании поставщика данных MSOLAP, задать источник данных в строке подключения на имя сервера и значение исходного каталога имя каталога из источника данных. Чтобы подключиться к файлу куба, которая отсоединена от сервера, задайте местоположение полный путь. Файл, КУБ. В любом случае установите поставщик для имени поставщика. Например, следующая строка использует поставщик MSOLAP для подключения к каталогу, с именем Store Bobs видео на сервере с именем **Servername**:  
  
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
 [Пример объекта Cellset (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Метод Open (многомерные объекты ADO)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
