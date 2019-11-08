---
title: Коды возврата | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 36f376710dbcdd09daf664e9eee20533c5372641
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790233"
---
# <a name="return-codes"></a>Коды возврата
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для краткости можно сказать, что вызов функции-члена класса или структуры завершается успешно либо с ошибкой. Точнее сказать, вызов функции может оказаться успешным, но результат оказывается не таким, на какой рассчитывал разработчик приложения.  
  
 Дополнительные сведения о кодах возврата OLE DB см. в статье [Коды возврата (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Когда функция-член поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB возвращает S_OK, функция прошла удачно.  
  
 Если функция-член поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не возвращает S_OK, то в случае сбоя OLE/COM HRESULT-распаковки и IS_ERROR макросы могут определить общую успешность или сбой функции.  
  
 Если сбой или IS_ERROR возвращает значение TRUE, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент поставщика OLE DB клиента гарантирует, что выполнение функции-члена не удалось. Если сбой или IS_ERROR возвращают значение FALSE, а значение HRESULT не равно S_OK, потребитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB поставщика гарантирует, что функция была успешно выполнена в определенном смысле. Потребитель может получить подробные сведения об этом возвращении из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB интерфейсах ошибок поставщика. Кроме того, в случае, когда функция явно завершается неудачей (макрос FAILed возвращает значение TRUE), расширенные сведения об ошибке доступны из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейсов ошибок поставщика собственного клиента OLE DB.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB_S_ERRORSOCCURRED для потребителей собственного клиента OLE DB поставщика обычно встречается возвращаемое значение HRESULT "Success with Information". Функции-члены, возвращающие значение DB_S_ERRORSOCCURRED, обычно определяют один или несколько параметров, предоставляющих потребителю значения состояния. Информация, возвращаемая через параметры состояния, может быть единственной информацией о состоянии, доступной потребителю; поэтому для получения значений состояния, когда они доступны, потребители должны реализовать собственную логику приложения.  
  
 Функции члена поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB не возвращают код успешного S_FALSE. Все функции члена поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB всегда возвращают S_OK, чтобы указать на успешное выполнение.  
  
## <a name="see-also"></a>См. также раздел  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
