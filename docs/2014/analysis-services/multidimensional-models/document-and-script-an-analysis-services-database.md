---
title: Document and Script an Analysis Services Database | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d46180c78befec8a55f03d2064aaa6b94e2ba6a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165497"
---
# <a name="document-and-script-an-analysis-services-database"></a>Документирование и работа со скриптами в базе данных служб Analysis Services
  После того как база данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развернута, вы можете использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для вывода метаданных базы данных или объекта, содержащегося в ней, в качестве скрипта XML для аналитики (XMLA). Можно вывести этот скрипт в новое окно **Редактор запросов XML для аналитики** , в файл или в буфер обмена. Дополнительные сведения о XML для Аналитики, см. в разделе [язык сценариев служб Analysis Services &#40;ASSL&#41; ссылку](../scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Сформированный скрипт XML для аналитики использует элементы языка скриптов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (ASSL) для определения объектов, содержащихся в скрипте. Если создан скрипт CREATE, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Создать** и элементы ASSL, которые могут быть использованы для создания всей структуры базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в экземпляре. Если создан скрипт ALTER, результирующий скрипт XML для аналитики будет содержать команду XML для аналитики **Изменить** и элементы ASSL, которые могут быть использованы для восстановления структуры существующей базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в состояние, в котором она находилась на момент создания скрипта.  
  
 Созданный скрипт XML для аналитики из базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно использовать различными способами, в том числе:  
  
-   для поддержки скрипта резервного копирования, который позволяет повторно создавать разрешения и объекты базы данных;  
  
-   для создания или обновления кода разработки базы данных;  
  
-   для создания тестовой среды или среды разработки по существующей схеме.  
  
## <a name="see-also"></a>См. также  
 [Изменение или удаление базы данных служб Analysis Services](modify-or-delete-an-analysis-services-database.md)   
 [Элемент ALTER &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/alter-element-xmla.md)   
 [Создать элемент &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/create-element-xmla.md)  
  
  
