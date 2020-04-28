---
title: Использование служб компонентов Майкрософт | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb5763058fa198cbad7464434e31942ef8d6cd7d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307585"
---
# <a name="using-microsoft-component-services"></a>Использование служб компонентов Майкрософт
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Можно включить базу данных Oracle для работы со службами транзакционных компонентов (или MTS, если используется Windows NT) в Microsoft Windows NT, Windows 2000 и Microsoft Windows 95/98. Чтобы обеспечить работу базы данных Oracle со службами компонентов, которые поддерживают транзакции, системным администраторам следует создать представление с именем V $ КСАТРАНС $. Чтобы создать этот скрипт, необходимо выполнить скрипт, предоставляемый Oracle. Дополнительные сведения см. в справке по службам компонентов или в документации Oracle.
