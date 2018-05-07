---
title: 'Шаг 1: Подключение к источнику данных | Документы Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98fff3a58b7bc191b275d4f887f5856700f7fa91
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="step-1-connect-to-the-data-source"></a>Шаг 1: Подключение к источнику данных
Для подключения к источнику данных является первым шагом в любом приложении. Этот этап, включая функции, необходимые, показан на следующем рисунке.  
  
 ![Подключение к источнику данных в приложении ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Первым шагом в соединении с источником данных является для загрузки диспетчера драйверов и выделить дескриптор среды с **SQLAllocHandle**. Дополнительные сведения см. в разделе [выделения памяти для обработки среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Затем приложение регистрирует используемая версия ODBC, в которой он соответствует путем вызова **SQLSetEnvAttr** с атрибутом SQL_ATTR_APP_ODBC_VER среды. Дополнительные сведения см. в разделе [объявление приложения ODBC версии](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) и [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 После этого приложение выделяет дескриптор соединения с **SQLAllocHandle** и подключается к источнику данных с **SQLConnect**, **SQLDriverConnect**, или **SQLBrowseConnect**. Дополнительные сведения см. в разделе [выделения дескриптор подключения](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) и [подключения](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Затем приложение задает любых атрибутов соединения, такие как вручную фиксации транзакции. Дополнительные сведения см. в разделе [атрибуты соединения](../../../odbc/reference/develop-app/connection-attributes.md).
