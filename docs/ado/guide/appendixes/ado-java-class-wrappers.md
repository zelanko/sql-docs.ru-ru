---
title: Классы-оболочки Java ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 840d8a0e266a6f913a8a74ec1451bc6285fbb08b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47729222"
---
# <a name="ado-java-class-wrappers"></a>Классы-оболочки Java для объектов ADO
Этот код объявляет экземпляр ADO [записей](../../../ado/reference/ado-api/recordset-object-ado.md) оболочки класса и инициализирует его, все в одной строке кода. Кроме того, он объявляет переменные для каждого аргумента в [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод, особенно для [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) и [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) (так как Java не поддерживает перечисленные типы). Он открывает и закрывает **записей** объекта. Задав Rs1 NULL просто планирует эту переменную, чтобы освободить после ее выпуска систематический и с периодической неиспользуемых объектов выполняет Java.  
  
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
