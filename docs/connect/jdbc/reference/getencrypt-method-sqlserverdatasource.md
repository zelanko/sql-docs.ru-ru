---
title: Метод getEncrypt (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3764ff5b9308b4b370dda14e98787513c28458c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67983376"
---
# <a name="getencrypt-method-sqlserverdatasource"></a>Метод getEncrypt (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение типа **Boolean**, определяющее, включено ли свойство encrypt.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если шифрование включено. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если для свойства encrypt задано значение **true**, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] обеспечивает в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL-шифрование всех данных, передаваемых между клиентом и сервером при условии, что на сервере установлен сертификат.  
  
 Если свойство encrypt не указано или имеет значение **false**, то драйвер не будет принудительно выполнять в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержку SSL-шифрования. Если в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не настроено принудительное выполнение SSL-шифрования, то подключение устанавливается без применения шифрования. Если в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] настроено принудительное SSL-шифрование, то [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] автоматически включит SSL-шифрование при запуске на правильно настроенной виртуальной машине Java, в противном случае подключение будет разорвано, а драйвер вернет ошибку. Если свойство шифрования не задано, метод [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) возвращает значение по умолчанию **false**.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
