---
title: С помощью служб компонентов Майкрософт | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], component services
- component services [ODBC]
ms.assetid: 06450562-d8f3-4987-b7bd-4a70223ff937
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91d6dcf0ca7f87d6ed510d582f7a7ba0f80e8c74
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088152"
---
# <a name="using-microsoft-component-services"></a>Использование служб компонентов Майкрософт
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Вы можете включить базы данных Oracle для работы с транзакционной службы компонентов (или MTS, если вы используете Windows NT) на базе Microsoft Windows NT или Windows 2000 и Microsoft Windows 95/98. Чтобы включить базы данных Oracle для работы со службами компонента, который поддерживает транзакции, системные администраторы должны создать представление V$ XATRANS$. Чтобы создать этот сценарий, необходимо запустить сценарий, предоставляемый Oracle. Дополнительные сведения см. в справке служб компонентов или документации Oracle.
