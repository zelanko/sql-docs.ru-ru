---
title: Коды возврата | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 625d56a38d88b3cccbea1c75ad88917af1a6f6dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63228943"
---
# <a name="return-codes"></a>Коды возврата
  Для краткости можно сказать, что вызов функции-члена класса или структуры завершается успешно либо с ошибкой. Точнее сказать, вызов функции может оказаться успешным, но результат оказывается не таким, на какой рассчитывал разработчик приложения.  
  
 Дополнительные сведения о кодах возврата OLE DB см. в статье [Коды возврата (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Когда функция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -член поставщика собственного клиента OLE DB возвращает S_OK, функция прошла удачно.  
  
 Когда функция [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -член поставщика собственного клиента OLE DB не возвращает S_OK, ошибка HRESULT OLE/COM-распаковки, а IS_ERROR макросы могут определить общую успешность или сбой функции.  
  
 Если сбой или IS_ERROR возвращает значение TRUE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель поставщика OLE DB собственного клиента гарантирует, что выполнение функции-члена завершилось ошибкой. Если сбой или IS_ERROR возвращают значение FALSE, а значение HRESULT не равно S_OK [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , потребитель поставщика OLE DB собственного клиента гарантирует, что функция была успешно выполнена в определенном смысле. Потребитель может получить подробную информацию о возврате данных об успешном выполнении с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB интерфейсах ошибок поставщика. Кроме того, в случае, когда функция явно завершается неудачей (макрос FAILed возвращает значение TRUE), расширенные сведения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] об ошибке можно получить из собственного клиента OLE DB интерфейсы ошибок поставщика.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Потребители собственного клиента OLE DB поставщика обычно сталкиваются с возвратом DB_S_ERRORSOCCURRED "Success with Information". Функции-члены, возвращающие значение DB_S_ERRORSOCCURRED, обычно определяют один или несколько параметров, предоставляющих потребителю значения состояния. Информация, возвращаемая через параметры состояния, может быть единственной информацией о состоянии, доступной потребителю; поэтому для получения значений состояния, когда они доступны, потребители должны реализовать собственную логику приложения.  
  
 Функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] члена поставщика собственного клиента OLE DB не возвращают код успешного выполнения S_FALSE. Все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функции члена поставщика собственного клиента OLE DB всегда возвращают S_OK, чтобы указать на успешное выполнение.  
  
## <a name="see-also"></a>См. также:  
 [ошибки](errors.md)  
  
  
