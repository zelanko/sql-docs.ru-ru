---
title: Класс SQLServerXAResource | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 64d2ae6fe7e4e57774dc75c34fc61ab680e99434
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
