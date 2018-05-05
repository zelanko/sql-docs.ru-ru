---
title: Метод getEncrypt (SQLServerDataSource) | Документы Microsoft
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
ms.openlocfilehash: 2fcc6ba50954f45d88bb16d1a5ba065d59cf0f57
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
