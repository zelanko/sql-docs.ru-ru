---
title: Большие определяемые пользователем типы данных CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 878d68858a75bd6e26adbc8080e8956b3a8a061d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761379"
---
# <a name="large-clr-user-defined-types"></a>Большие определяемые пользователем типы данных CLR
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В SQL Server 2005 определяемые пользователем типы данных (UDT) в среде CLR были ограничены размером в 8000 байт. Это ограничение было снято в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версиях. Теперь определяемые пользователем типы данных CLR обрабатываются подобно типам больших объектов (LOB). То есть объекты определяемого пользователем типа размером не более 8000 байт ведут себя так же, как в SQL Server 2005, но такие же объекты большего размера поддерживаются и сообщают о своем размере как о неограниченном.  
  
 Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных clr &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md) и [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="use-cases"></a>Варианты использования  
 Для ODBC поддержка больших объектов определяемого пользователем типа включает в себя возможность отправить значения определяемого пользователем типа по частям как параметры с данными времени выполнения. Это делается с помощью SQLPutData.  
  
 Для OLE DB поддержка больших пользовательских типов включает в себя возможность передать потоком значения пользовательского типа на сервер и обратно с помощью привязки ISequentialStream.  
  
 Определяемые пользователем типы размером меньше или равным 8 000 байт будут вести себя так же, как в SQL Server 2005. Для OLE DB можно по-прежнему выполнять потоковую передачу небольших определяемых пользователем типов с помощью привязки ISequentialStream.  
  
 Иногда собственному коду будет необходимо понять содержимое определяемых пользователем типов CLR, но не придется создавать экземпляр управляющего объекта. В таком случае можно использовать пользовательскую сериализацию для преобразования на сервере значений определяемых пользователем типов в хорошо знакомый клиенту формат.  
  
 Для приложений, имеющих существующий код доступа к данным, можно использовать поведение определяемых пользователем типов CLR на клиенте путем получения определяемых пользователем типов через собственные API-интерфейсы и создания их экземпляров при помощи CLI-взаимодействия языка C++ в приложениях смешанного режима.  
  
## <a name="see-also"></a>См. также:  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
