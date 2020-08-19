---
description: Шаг 1. Подключение к источнику данных
title: Шаг 1. подключение к источнику данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac15eed6c84745dca6406ad8186f14c65798939
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482967"
---
# <a name="step-1-connect-to-the-data-source"></a>Шаг 1. Подключение к источнику данных
Первым шагом в любом приложении является подключение к источнику данных. Этот этап, включая необходимые функции, показан на следующем рисунке.  
  
 ![Подключение к источнику данных в приложении ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Первым шагом при подключении к источнику данных является загрузка диспетчера драйверов и выделение обработчика среды с помощью **функцию SQLAllocHandle**. Дополнительные сведения см. [в разделе Выделение маркера среды](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Затем приложение регистрирует версию ODBC, в которой она соответствует, вызывая **SQLSetEnvAttr** с атрибутом среды SQL_ATTR_APP_ODBC_VER. Дополнительные сведения см. [в разделе Объявление версии ODBC приложения](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) и [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Затем приложение выделяет маркер подключения с помощью **функцию SQLAllocHandle** и подключается к источнику данных с помощью **SQLConnect**, **SQLDriverConnect**или **SQLBrowseConnect**. Дополнительные сведения см. в разделе [Выделение маркера подключения](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) и [Установка соединения](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Затем приложение устанавливает любые атрибуты соединения, например, следует ли вручную фиксировать транзакции. Дополнительные сведения см. в разделе [атрибуты соединения](../../../odbc/reference/develop-app/connection-attributes.md).
