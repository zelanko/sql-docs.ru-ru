---
title: Метод getEncrypt (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9262c2fb18160f5072d21a71c082bd00d17fc302
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32835009"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>Метод getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **логическое** значение, указывающее, включено ли свойство encrypt.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если шифрование включено. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойству encrypt присвоено **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] гарантирует, что [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] использует шифрование SSL для всех данных, передаваемых между клиентом и сервером, если сервер имеет установленный сертификат.  
  
 Если свойство шифрования не задано или равно **false**, драйвер не будет применять [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] поддержку SSL-шифрования. Если [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] экземпляр не настроен на принудительное шифрование протокола SSL, то соединение устанавливается без применения шифрования. Если [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] экземпляре настроено принудительное SSL-шифрования, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет автоматически включить SSL-шифрование при запуске на правильно настроенной виртуальной машины Java (JVM), иначе соединение будет разорвано и в работе драйвера будет вызвана Произошла ошибка. Если свойство шифрования не задано, [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) метод возвращает значение по умолчанию **false**.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
