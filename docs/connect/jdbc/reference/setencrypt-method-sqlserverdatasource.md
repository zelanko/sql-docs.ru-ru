---
title: Метод setEncrypt (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setEncrypt Method (SQLServerDataSource)
apilocation:
- setEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 0c85a9c1-f27c-457e-8461-403cc03e2d17
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da0aa987f1ec773e2f61e738bc4045136c64859a
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219243"
---
# <a name="setencrypt-method-sqlserverdatasource"></a>Метод setEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение типа **Boolean**, определяющее, включено ли свойство encrypt.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setEncypt(boolean encrypt)  
```  
  
#### <a name="parameters"></a>Параметры  
 *encrypt*  
  
 Значение **true**, если между клиентом и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включено шифрование TLS, ранее называемое шифрованием SSL. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если для свойства encrypt задано значение **true**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] обеспечивает в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] шифрование TLS всех данных, передаваемых между клиентом и сервером при условии, что на сервере установлен сертификат. Значение по умолчанию — **false**.  
  
 При выполнении TLS-подтверждения драйвер JDBC определяет виртуальную машину Java (JVM), на которой он запущен.  
  
 Если для свойства "encrypt" задано значение **true**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] использует настроенный по умолчанию поставщик безопасности JSSE в виртуальной машине Java, чтобы согласовать TLS-шифрование с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Поставщик безопасности по умолчанию может не поддерживать все функции, необходимые для успешного согласования TLS-шифрования. Например, поставщик безопасности по умолчанию может не поддерживать размер открытого ключа RSA, используемого в TLS/SSL-сертификате [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. В этом случае поставщик безопасности по умолчанию может вызвать ошибку, в результате которой драйвер JDBC разорвет соединение. Чтобы устранить эту неполадку, выполните одно из следующих действий.  
  
-   Настройте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с сертификатом сервера, имеющим открытый ключ RSA меньшего размера  
  
-   Настройте в виртуальной машине Java другой поставщик безопасности JSSE в файле свойств безопасности "\<java-home>/lib/security/java.security"  
  
-   Используйте другой JVM  
  
 Если свойство encrypt не указано или имеет значение **false**, то драйвер не будет принудительно применять в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержку шифрования TLS. Если в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не настроено принудительное шифрование TLS, то подключение устанавливается без применения шифрования. Если в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] настроено принудительное шифрование TLS, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] автоматически включит шифрование TLS при запуске на корректно настроенной виртуальной машине Java (JVM). В противном случае соединение будет прервано, а драйвер выдаст ошибку.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
