---
description: Классы-оболочки Java для объектов ADO
title: Оболочки классов ADO Java | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: rothja
ms.author: jroth
ms.openlocfilehash: c02865fc20d741fc8b3f80ccecd56fcb105ad45e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355220"
---
# <a name="ado-java-class-wrappers"></a>Классы-оболочки Java для объектов ADO
Этот код объявляет экземпляр оболочки класса [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) ADO и инициализирует его в той же строке кода. Кроме того, он объявляет переменные для каждого аргумента в методе [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) , особенно для [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) и [примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (так как Java не поддерживает перечислимые типы). Он открывает и закрывает объект **Recordset** . Если для параметра Rs1 задать значение NULL, то только запланирует освобождение этой переменной, когда Java выполняет систематический и периодический выпуск неиспользуемых объектов.  
  
```java
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование пакета Microsoft SDK для Java](../../../ado/guide/appendixes/using-the-microsoft-sdk-for-java.md)
