---
title: Метод setTrustServerCertificate (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a5c2ea95878abc101032eb662a601a65047c1e1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902077"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Метод setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение типа **Boolean**, определяющее, включено ли свойство trustServerCertificate.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Параметры  
 *trustServerCertificate*  
  
 Значение **true**, если SSL-сертификат должен автоматически считаться доверенным, когда на уровне связи применяется SSL-шифрование. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если свойство trustServerCertificate имеет значение **true**, то SSL-сертификат [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] автоматически считается доверенным, когда на уровне связи применяется SSL-шифрование. Иными словами, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] не будет выполнять проверку SSL-сертификата [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Значение по умолчанию — **false**.  
  
 Если свойство trustServerCertificate имеет значение **false**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет проверять SSL-сертификат сервера.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
