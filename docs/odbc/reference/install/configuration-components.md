---
description: Компоненты конфигурации
title: Компоненты конфигурации | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a8a4b0f0b0a7a99409b5bb9caea53f23b62457e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487437"
---
# <a name="configuration-components"></a>Компоненты конфигурации
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Источники данных настраиваются библиотекой DLL установщика, которая, в свою очередь, вызывает библиотеки DLL установки драйвера и библиотеки DLL установки переводчиков по мере необходимости. Библиотека DLL установщика вызывается непосредственно из панели управления или загружается и вызывается другой программой, называемой *программой администрирования*. На следующем рисунке показана связь между компонентами конфигурации.  
  
 ![Связь между компонентами конфигурации](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Дополнительные сведения об этих компонентах см. в следующих разделах в конце этого раздела.  
  
-   [Программа установки](../../../odbc/reference/install/setup-program.md)  
  
-   [Библиотека DLL установщика](../../../odbc/reference/install/installer-dll.md)  
  
-   [Библиотека DLL программы установки драйвера](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>См. также:  
 [Компоненты установки](../../../odbc/reference/install/installation-components.md)
