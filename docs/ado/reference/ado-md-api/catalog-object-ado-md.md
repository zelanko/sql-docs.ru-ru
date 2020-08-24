---
description: Объект Catalog (многомерные объекты ADO)
title: Объект каталога (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog
helpviewer_keywords:
- Catalog object [ADO MD]
ms.assetid: 11f6f896-d69c-44a4-94cd-d54c93140e4a
author: rothja
ms.author: jroth
ms.openlocfilehash: b198e9765a8d0e68e61ecd3f9ed334e34c714ea8
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778343"
---
# <a name="catalog-object-ado-md"></a>Объект Catalog (многомерные объекты ADO)
Содержит сведения о многомерной схеме (то есть Кубы и базовые измерения, иерархии, уровни и элементы), относящиеся к поставщику многомерных данных (MDP).  
  
## <a name="remarks"></a>Remarks  
 С помощью коллекций и свойств объекта **каталога** можно выполнять следующие действия.  
  
-   Откройте каталог, задав для свойства [ActiveConnection](./activeconnection-property-ado-md.md) стандартный объект [соединения](../ado-api/connection-object-ado.md) ADO или допустимую строку подключения.  
  
-   Найдите **Каталог** со свойством [Name](./name-property-ado-md.md) .  
  
-   Выполните итерацию по кубам в каталоге, используя коллекцию [кубедефс](./cubedefs-collection-ado-md.md) .  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](./catalog-object-properties-methods-and-events-ado-md.md)  
  
## <a name="see-also"></a>См. также  
 [Пример каталога (VB)](./catalog-example-vb.md)   
 [Объект Connection (ADO)](../ado-api/connection-object-ado.md)   
 [Коллекция CubeDefs (многомерные объекты ADO)](./cubedefs-collection-ado-md.md)