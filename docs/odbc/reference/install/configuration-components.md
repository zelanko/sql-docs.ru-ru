---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 248a9e31b176444ad51cb3a62c7c5f12f1b7bde3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068577"
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
