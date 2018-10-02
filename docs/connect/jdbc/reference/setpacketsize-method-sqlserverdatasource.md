---
title: Метод setPacketSize (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d2346b1d64db708a94c45ac1a643d2dfcaf5fed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694940"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Метод setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает текущий размер сетевого пакета в байтах, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Параметры  
 *packetSize*  
  
 Значение типа **int**, содержащее размер сетевого пакета.  
  
## <a name="remarks"></a>Remarks  
 Диапазон допустимых значений этого свойства: [-1 | 0 | 512..32767]. Если этому свойству задано значение за пределами допустимого диапазона значений, возникнет исключение.  
  
 Приложению может понадобиться задать свойство packetSize во время соединения с шифрованием SSL. [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] согласовывает размер пакета с сервером. Если свойство encrypt имеет значение "**true**", а согласованный размер пакета превышает размер записи SSL поставщика безопасности по умолчанию для виртуальной машины Java (JVM), то драйвер вызывает ошибку и завершает подключение.  
  
 Кроме того, приложению может понадобиться задавать свойство packetSize без запроса шифрования SSL. В этом случае, если сервер требует от клиента поддержку шифрования SSL, драйвер проверяет размер записи SSL поставщика безопасности по умолчанию для JVM. Если свойство packetSize превышает размер записи SSL поставщика безопасности по умолчанию для JVM, то драйвер вызывает ошибку и завершает соединение.  
  
 Дополнительные сведения об использовании SSL см. в разделе [с помощью SSL-шифрование](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
