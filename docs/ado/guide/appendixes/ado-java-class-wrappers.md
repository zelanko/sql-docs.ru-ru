---
title: "ADO Java классов-оболочек | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 08cbd288ba9f64816ae0c8fd62c18171967c4d0d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
## <a name="see-also"></a>См. также:  
 [С помощью пакета Microsoft SDK для Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)

