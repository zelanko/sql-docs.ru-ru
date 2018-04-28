---
title: Метод setPacketSize (SQLServerDataSource) | Документы Microsoft
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
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5aa6b33545077b93cb23dde9a239a83662a9c5b4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Метод setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает текущий размер сетевого пакета, используемый для связи с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], указанного в байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Размер_пакета*  
  
 **Int** значение, содержащее размер сетевого пакета.  
  
## <a name="remarks"></a>Замечания  
 Диапазон допустимых значений этого свойства: [-1 | 0 | 512..32767]. Если этому свойству задано значение за пределами допустимого диапазона значений, возникнет исключение.  
  
 Приложению может понадобиться задать свойство packetSize во время соединения с шифрованием SSL. [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Согласует размер пакета с сервером. Если свойство encrypt имеет значение «**true**» и согласованный размер пакета превышает размер записи SSL поставщика для виртуальной машины Java (JVM) по умолчанию безопасности, драйвер будет возвращает ошибку и завершает соединение.  
  
 Кроме того, приложению может понадобиться задавать свойство packetSize без запроса шифрования SSL. В этом случае, если сервер требует от клиента поддержку шифрования SSL, драйвер проверяет размер записи SSL поставщика безопасности по умолчанию для JVM. Если свойство packetSize превышает размер записи SSL поставщика безопасности по умолчанию для JVM, то драйвер вызывает ошибку и завершает соединение.  
  
 Дополнительные сведения об использовании SSL см. в разделе [с помощью SSL-шифрования](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
