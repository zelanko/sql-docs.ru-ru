---
description: Метод getTrustServerCertificate (SQLServerDataSource)
title: Метод getTrustServerCertificate (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3a5de057e6a9363f4e3feeace35f2b5105d3cd3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434056"
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>Метод getTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение типа **Boolean**, определяющее, включено ли свойство trustServerCertificate.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если свойство trustServerCertificate включено. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если значение свойства trustServerCertificate равно **true**, TLS-сертификат, ранее называемый SSL-сертификатом, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] автоматически считается доверенным, когда для шифрования уровня связи используется TLS. Иными словами, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не будет выполнять проверку TLS/SSL-сертификата [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Значение по умолчанию — **false**.  
  
 Если свойство trustServerCertificate имеет значение **false**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет проверять TLS/SSL-сертификат сервера.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
