---
title: Класс SQLServerXAResource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8cde4f1b80ae1167ba7f99c80505e3b838890113
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66768346"
---
# <a name="sqlserverxaresource-class"></a>Класс SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет интерфейс XAResource для управления распределенными транзакциями XA.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** java.lang.Object  
  
 **Реализует:** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>Remarks  
 Транзакции XA реализуются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] путем использования диспетчера распределенных транзакций (DTC) [!INCLUDE[msCoName](../../../includes/msconame_md.md)]. Класс SQLServerXAResource вызывает методы расширенной библиотеки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с именем sqljdbc_xa.dll, которая служит интерфейсом для DTC. Вызовы XA, получаемые SQLServerXAResource (XA_START, XA_END, XA_PREPARE и т. д.), сопоставляются с соответствующими вызовами функций DTC.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
