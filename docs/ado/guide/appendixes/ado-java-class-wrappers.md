---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70486a27cfbe5c977d371906da89563059685093
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67927004"
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
