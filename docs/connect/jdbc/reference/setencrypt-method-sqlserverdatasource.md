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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 248213fed555ffc029162c44bdcccb656c311703
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67974286"
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
  
 Значение **true**, если шифрование по протоколу SSL при взаимодействии клиента и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включено. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если свойство encrypt имеет значение **true**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] обеспечивает в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL-шифрование для всех данных, передаваемых между клиентом и сервером при условии, что на сервере установлен сертификат. Значение по умолчанию — **false**.  
  
 При выполнении SSL-подтверждения драйвер JDBC определяет виртуальную машину Java (JVM), на которой он запущен.  
  
 Если для свойства "encrypt" задано значение **true**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] использует настроенный по умолчанию поставщик безопасности JSSE в виртуальной машине Java, чтобы согласовать SSL-шифрование с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Поставщик безопасности по умолчанию может не поддерживать все функции, необходимые для успешного согласования SSL-шифрования. Например, поставщик безопасности по умолчанию может не поддерживать размер открытого ключа RSA, используемого в SSL-сертификате [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. В этом случае поставщик безопасности по умолчанию может вызвать ошибку, в результате которой драйвер JDBC разорвет соединение. Чтобы устранить эту неполадку, выполните одно из следующих действий.  
  
-   Настройте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с сертификатом сервера, имеющим открытый ключ RSA меньшего размера  
  
-   Настройте в виртуальной машине Java другой поставщик безопасности JSSE в файле свойств безопасности "\<java-home>/lib/security/java.security"  
  
-   Используйте другой JVM  
  
 Если свойство encrypt не указано или имеет значение **false**, то драйвер не будет принудительно выполнять в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержку SSL-шифрования. Если в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не настроено принудительное выполнение SSL-шифрования, то подключение устанавливается без применения шифрования. Если в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включено принудительное SSL-шифрование, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] автоматически включит шифрование при запуске на правильно настроенной виртуальной машине Java. В противном случае подключение будет разорвано и драйвер сообщит об ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
