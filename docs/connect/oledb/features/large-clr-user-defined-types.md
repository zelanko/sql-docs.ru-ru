---
title: Определяемые пользователем типы больших значений CLR | Документация Майкрософт
description: Большие определяемые пользователем типы CLR в драйвер OLE DB для SQL Server
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
manager: jroth
ms.openlocfilehash: dedc82c4f1b2189e3752562e461f270cc0f5c4bf
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66766054"
---
# <a name="large-clr-user-defined-types"></a>Большие определяемые пользователем типы данных CLR
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  В SQL Server 2005 определяемые пользователем типы данных (UDT) в среде CLR были ограничены размером в 8000 байт. Это ограничение было снято в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версиях. Теперь определяемые пользователем типы данных CLR обрабатываются подобно типам больших объектов (LOB). То есть объекты определяемого пользователем типа размером не более 8000 байт ведут себя так же, как в SQL Server 2005, но такие же объекты большего размера поддерживаются и сообщают о своем размере как о неограниченном.  
  
 Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;OLE DB&#41;](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md).  
  
## <a name="use-cases"></a>Способы применения   
  
 Для OLE DB поддержка больших пользовательских типов включает в себя возможность передать потоком значения пользовательского типа на сервер и обратно с помощью привязки ISequentialStream.  
  
 Определяемые пользователем типы размером меньше или равным 8 000 байт будут вести себя так же, как в SQL Server 2005. Для OLE DB вы можете по-прежнему передавать маленьких определяемых пользователем типов с помощью интерфейса ISequentialStream привязки.  
  
 Иногда собственному коду будет необходимо понять содержимое определяемых пользователем типов CLR, но не придется создавать экземпляр управляющего объекта. В таком случае можно использовать пользовательскую сериализацию для преобразования на сервере значений определяемых пользователем типов в хорошо знакомый клиенту формат.  
  
 Для приложений, имеющих существующий код доступа к данным, можно использовать поведение определяемых пользователем типов CLR на клиенте путем получения определяемых пользователем типов через собственные API-интерфейсы и создания их экземпляров при помощи CLI-взаимодействия языка C++ в приложениях смешанного режима.  
  
## <a name="see-also"></a>См. также:  
 [Возможности драйвера OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
