---
title: Метод getTrustServerCertificate (SQLServerDataSource) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 81d07743dfefe0b0305b1a094a9ae4632d4effd9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978580"
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
 Если значение свойства trustServerCertificate равно **true**, SSL-сертификат [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] автоматически считается доверенным, когда для шифрования уровня связи используется SSL. Иными словами, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не будет выполнять проверку SSL-сертификата [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Значение по умолчанию — **false**.  
  
 Если свойство trustServerCertificate имеет значение **false**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет проверять SSL-сертификат сервера.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
