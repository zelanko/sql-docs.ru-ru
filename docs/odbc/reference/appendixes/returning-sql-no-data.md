---
title: Возврат SQL_NO_DATA | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2f731589dcbc10d24ff42d895db60f9f8c054de
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794184"
---
# <a name="returning-sqlnodata"></a>Возврат SQL_NO_DATA
Когда ODBC *2.x* workingwith приложения ODBC *3.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или  **SQLParamData**, и поисковое обновление или инструкции delete был выполнен, но не влияют на все строки в источнике данных ODBC *3.x* драйвер должен возвращать значение SQL_SUCCESS. Когда ODBC *3.x* приложение, которое работает с ODBC *3.x* драйвер вызывает **SQLExecDirect**, **SQLExecute**, или  **SQLParamData** с тем же ODBC *3.x* драйвер вернет значение SQL_NO_DATA.  
  
 Искомая инструкция update или delete в пакет инструкций не влияет на все строки в источнике данных, **SQLMoreResults** возвращает значение SQL_SUCCESS. Он не может возвращать значение SQL_NO_DATA, так как это будет означать, что нет больше результатов, не, что является результатом из поисковое обновление, удаление, затрагиваются ни одной строки.
