---
title: 'Шаг 1: Подключение к источнику данных (ru) Документы Майкрософт'
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
ms.openlocfilehash: 2a104733c0e5ec5acc87eeabd00c4e51d4bfd000
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301354"
---
# <a name="step-1-connect-to-the-data-source"></a>Шаг 1. Подключение к источнику данных
Первым шагом в любом приложении является подключение к источнику данных. Эта фаза, включая необходимые функции, показана на следующей иллюстрации.  
  
 ![Подключение к источнику данных в приложении ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Первым шагом в подключении к источнику данных является загрузка менеджера драйвера и выделение обработки среды с **помощью S'LAllocHandle.** Для получения дополнительной [Allocating the Environment Handle](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)информации см.  
  
 Затем приложение регистрирует версию ODBC, которой оно соответствует, позвонив в **s'LSetEnvAttr** с SQL_ATTR_APP_ODBC_VER атрибутом среды. Для получения дополнительной [информации](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md) [см.](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)  
  
 Далее приложение выделяет ручку соединения с **s'LAllocHandle** и подключается к исходую кода с **помощью S'LConnect,** **S'LDriverConnect**или **S'LBrowseConnect.** Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) [Establishing a Connection](../../../odbc/reference/develop-app/establishing-a-connection.md)  
  
 Затем приложение устанавливает любые атрибуты соединения, например, следует ли вручную совершать транзакции. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/connection-attributes.md)
