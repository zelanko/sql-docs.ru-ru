---
title: Коды возврата | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 37f3326aacd601dd9b52f0f55e146fa1b17cdcc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086893"
---
# <a name="return-codes"></a>Коды возврата
  Для краткости можно сказать, что вызов функции-члена класса или структуры завершается успешно либо с ошибкой. Точнее сказать, вызов функции может оказаться успешным, но результат оказывается не таким, на какой рассчитывал разработчик приложения.  
  
 Дополнительные сведения о кодах возврата OLE DB см. в разделе [коды возврата (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция-член поставщика OLE DB для собственного клиента возвращает S_OK, вызов функции был успешным.  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция-член поставщика OLE DB для собственного клиента не возвращает значение S_OK, макросы распаковки HRESULT OLE/COM FAILED и IS_ERROR можно определить общий успех или сбой функции.  
  
 Если макрос FAILED или IS_ERROR возвращает значение TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента уверен, что выполнение функции члена с ошибкой. Когда FAILED или IS_ERROR вернул значение FALSE, а значение HRESULT равно S_OK, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента уверен, что выполнение функции было в некотором смысле. Потребитель может получить подробные сведения, возвращаемые на этом «успеха с оговорками» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейсы ошибок поставщика OLE DB для собственного клиента. Кроме того, в случае, когда функции был явно неудачным (макрос FAILED возвращает значение TRUE), расширенные сведения об ошибке доступна из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейсы ошибок поставщика OLE DB для собственного клиента.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Потребители поставщика собственного клиента OLE DB часто сталкиваются возврата HRESULT DB_S_ERRORSOCCURRED «успеха с оговорками». Функции-члены, возвращающие значение DB_S_ERRORSOCCURRED, обычно определяют один или несколько параметров, предоставляющих потребителю значения состояния. Информация, возвращаемая через параметры состояния, может быть единственной информацией о состоянии, доступной потребителю; поэтому для получения значений состояния, когда они доступны, потребители должны реализовать собственную логику приложения.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Функции-члены поставщика OLE DB для собственного клиента не возвращают код успеха S_FALSE. Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функции-члены поставщика OLE DB для собственного клиента всегда возвращают S_OK в случае успеха.  
  
## <a name="see-also"></a>См. также  
 [ошибки](errors.md)  
  
  