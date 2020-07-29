---
title: Пользовательские типы больших данных в среде CLR | Документация Майкрософт
description: Использование типов больших данных среды CLR в OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 20469f3cd6a1b98a6fd08db195e883ccff4ac776
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006950"
---
# <a name="large-clr-user-defined-types"></a>Большие определяемые пользователем типы данных CLR
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В SQL Server 2005 определяемые пользователем типы данных (UDT) в среде CLR были ограничены размером в 8000 байт. Это ограничение было снято в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версиях. Теперь определяемые пользователем типы данных CLR обрабатываются подобно типам больших объектов (LOB). То есть объекты определяемого пользователем типа размером не более 8000 байт ведут себя так же, как в SQL Server 2005, но такие же объекты большего размера поддерживаются и сообщают о своем размере как о неограниченном.  
  
 См. сведения об [больших пользовательских типах CLR (OLE DB)](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md).  
  
## <a name="use-cases"></a>Варианты использования   
  
 Для OLE DB поддержка больших пользовательских типов включает в себя возможность передать потоком значения пользовательского типа на сервер и обратно с помощью привязки ISequentialStream.  
  
 Определяемые пользователем типы размером меньше или равным 8 000 байт будут вести себя так же, как в SQL Server 2005. Для OLE DB по-прежнему можно передавать потоком малые пользовательские типы, используя привязку ISequentialStream.  
  
 Иногда собственному коду будет необходимо понять содержимое определяемых пользователем типов CLR, но не придется создавать экземпляр управляющего объекта. В таком случае можно использовать пользовательскую сериализацию для преобразования на сервере значений определяемых пользователем типов в хорошо знакомый клиенту формат.  
  
 Для приложений, имеющих существующий код доступа к данным, можно использовать поведение определяемых пользователем типов CLR на клиенте путем получения определяемых пользователем типов через собственные API-интерфейсы и создания их экземпляров при помощи CLI-взаимодействия языка C++ в приложениях смешанного режима.  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
