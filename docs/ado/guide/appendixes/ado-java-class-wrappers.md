---
title: ADO Java классов-оболочек | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b77807fbdf03dd729f504e4112d205fb6cf7d6d6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="ado-java-class-wrappers"></a>ADO Java классов-оболочек
Этот код объявляет экземпляр ADO [записей](../../../ado/reference/ado-api/recordset-object-ado.md) оболочка класса и инициализирует его, все в одной строке кода. Кроме того, объявляет переменные для каждого аргумента в [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод, особенно для [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) и [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (поскольку Java не поддерживает перечисленные типы). Он открывается и закрывается **записей** объекта. Просто задав Rs1 NULL планирует этой переменной, освобождается, когда Java выполняет его систематического и периодически выпуск неиспользуемых объектов.  
  
```  
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Использование пакета Microsoft SDK для Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
