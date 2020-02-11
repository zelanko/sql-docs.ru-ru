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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91d6dcf0ca7f87d6ed510d582f7a7ba0f80e8c74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088152"
---
# <a name="using-microsoft-component-services"></a>Использование служб компонентов Майкрософт
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Можно включить базу данных Oracle для работы со службами транзакционных компонентов (или MTS, если используется Windows NT) в Microsoft Windows NT, Windows 2000 и Microsoft Windows 95/98. Чтобы обеспечить работу базы данных Oracle со службами компонентов, которые поддерживают транзакции, системным администраторам следует создать представление с именем V $ КСАТРАНС $. Чтобы создать этот скрипт, необходимо выполнить скрипт, предоставляемый Oracle. Дополнительные сведения см. в справке по службам компонентов или в документации Oracle.
