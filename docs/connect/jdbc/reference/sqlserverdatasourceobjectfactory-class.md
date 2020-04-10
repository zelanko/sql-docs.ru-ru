---
title: Класс SQLServerDataSourceObjectFactory | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 079ab64d487bf1ba09dd3bfeb2a89b4638c67674
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927597"
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Класс SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет фабрику объектов для материализации источников данных из интерфейса JNDI.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** java.lang.Object  
  
 **Реализует:** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Remarks  
 Этот метод наследуется всеми классами источников данных. В рамках поддержки интерфейса Referenceable [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] предоставляет доступ к этому классу, реализующему интерфейс ObjectFactory. Серверы приложений Java вызовут getReference для класса источников данных. В результате будет создан объект Reference, использующий имя класса внутри себя в качестве своей фабрики класса.  
  
 Если серверу Java Application требуется отменить ссылку на объект Reference, он создает экземпляр объекта SQLServerDataSourceObjectFactory и вызывает метод [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md), передавая объект Reference для извлечения экземпляра источника данных.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
