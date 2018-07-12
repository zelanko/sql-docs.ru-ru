---
title: Коды возврата | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00082a5c6053d8b9f0319c26ae8d72302c14d218
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407633"
---
# <a name="return-codes"></a>Коды возврата
  Для краткости можно сказать, что вызов функции-члена класса или структуры завершается успешно либо с ошибкой. Точнее сказать, вызов функции может оказаться успешным, но результат оказывается не таким, на какой рассчитывал разработчик приложения.  
  
 Дополнительные сведения о кодах возврата OLE DB, см. в разделе [коды возврата (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция-член поставщика OLE DB для собственного клиента вернет результат S_OK, функции был успешным.  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция-член поставщика OLE DB для собственного клиента не возвращает значение S_OK, макросов OLE/COM HRESULT-FAILED и IS_ERROR можно определить общий успех или сбой функции.  
  
 Если FAILED или IS_ERROR возвращает значение TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента уверен, что выполнение функции произошел сбой. Когда FAILED или IS_ERROR возвращают значение FALSE, а значение HRESULT не равно S_OK, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребителем поставщика OLE DB для собственного клиента уверен, что выполнение функции было в каком-то смысле. Потребитель может получить подробные сведения, возвращаемых на этот «успеха с оговорками» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейсы ошибок поставщика OLE DB для собственного клиента. Кроме того, в случае, когда функции был явно неудачным (макрос FAILED возвращает значение TRUE), сведения об ошибке доступна из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] интерфейсы ошибок поставщика OLE DB для собственного клиента.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Потребители поставщика собственного клиента OLE DB часто сталкиваются возврата HRESULT DB_S_ERRORSOCCURRED «успеха с оговорками». Функции-члены, возвращающие значение DB_S_ERRORSOCCURRED, обычно определяют один или несколько параметров, предоставляющих потребителю значения состояния. Информация, возвращаемая через параметры состояния, может быть единственной информацией о состоянии, доступной потребителю; поэтому для получения значений состояния, когда они доступны, потребители должны реализовать собственную логику приложения.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Функции-члены поставщика OLE DB для собственного клиента не возвращают код успеха S_FALSE. Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функции-члены поставщика OLE DB для собственного клиента всегда возвращают S_OK в случае успеха.  
  
## <a name="see-also"></a>См. также  
 [ошибки](errors.md)  
  
  
