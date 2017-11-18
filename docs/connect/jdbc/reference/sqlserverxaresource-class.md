---
title: "Класс SQLServerXAResource | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c5e0cb02544e0ea96c29758f7c50179de48cf7a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaresource-class"></a>Класс SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет XAResource для XA управления распределенными транзакциями.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** java.lang.Object  
  
 **Реализует:** javax.transaction.xa.XAResource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerXAResource  
```  
  
## <a name="remarks"></a>Замечания  
 Транзакции XA реализуются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] с помощью [!INCLUDE[msCoName](../../../includes/msconame_md.md)] диспетчера распределенных транзакций (DTC). Класс SQLServerXAResource вызывает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] расширенной библиотеки с именем Named sqljdbc_xa.dll, которая служит интерфейсом для DTC. Вызовы XA, получаемые SQLServerXAResource (XA_START, XA_END, XA_PREPARE и т. д.), сопоставляются с вызовами соответствующих функций DTC.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

