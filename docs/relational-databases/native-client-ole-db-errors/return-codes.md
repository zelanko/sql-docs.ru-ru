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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 09056c9d4964ad10b2b25f63ef5991a1a7742cab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301034"
---
# <a name="return-codes"></a>Коды возврата
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для краткости можно сказать, что вызов функции-члена класса или структуры завершается успешно либо с ошибкой. Точнее сказать, вызов функции может оказаться успешным, но результат оказывается не таким, на какой рассчитывал разработчик приложения.  
  
 Дополнительные сведения о кодах возврата OLE DB см. в статье [Коды возврата (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция поставщика NATIVE Client OLE DB возвращается S_OK, функция успешно.  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция поставщика услуг Native Client OLE DB не возвращается S_OK, распаковка НЕВРИМы и IS_ERROR макросов могут определить общий успех или сбой функции.  
  
 Если FAILED или IS_ERROR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает TRUE, потребитель-поставщик Native Client OLE DB уверен, что выполнение функции участника не выполнено. Когда FAILED или IS_ERROR возврат FALSE и HRESULT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не равняется S_OK, родной клиент OLE DB поставщик уверен, что функция удалось в некотором смысле. Потребитель может получить подробную информацию об этом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "успех с информацией" возвращение из Native Client OLE DB интерфейсов ошибка поставщика. Кроме того, в случае, если функция явно выходит из строя (макрос FAILED возвращает TRUE), расширенная информация об ошибках доступна из интерфейсов ошибок поставщика услуг [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Родные клиентole DB-провайдера потребители обычно сталкиваются с DB_S_ERRORSOCCURRED "успех с информацией" HRESULT возвращения. Функции-члены, возвращающие значение DB_S_ERRORSOCCURRED, обычно определяют один или несколько параметров, предоставляющих потребителю значения состояния. Информация, возвращаемая через параметры состояния, может быть единственной информацией о состоянии, доступной потребителю; поэтому для получения значений состояния, когда они доступны, потребители должны реализовать собственную логику приложения.  
  
 Функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика Native Client OLE DB не возвращают код успеха S_FALSE. Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функции поставщика Native Client OLE DB всегда возвращаются S_OK, чтобы показать успех.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
