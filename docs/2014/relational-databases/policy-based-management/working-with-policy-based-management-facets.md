---
title: Работа с аспектами управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d99e2dd074b283a9754f6fe7ee8e6f906595db13
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204444"
---
# <a name="working-with-policy-based-management-facets"></a>Работа с аспектами управления на основе политик
  Аспект управления на основе политик — это ряд логических свойств, которые связаны с определенной областью, представляющей интерес с точки зрения управления. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает несколько стандартных аспектов. Например, средство настройки контактной зоны, определяющее функции, отключенные по умолчанию.  
  
 При управлении несколькими похожими средами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить аспект в одном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], скопировать состояние аспекта в файл и импортировать этот файл на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве политики. При преобразовании состояния в политику она может быть применена к другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], объектам экземпляров, базам данных или объектам баз данных.  
  
 Этот раздел описывает способ копирования состояния аспекта в XML-файл.  
  
##  <a name="BeforeYouBegin"></a> Разрешения  
 Для процедуры в этом разделе требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="viewing-and-copying-facet-states"></a>Просмотр и копирование состояний аспекта  
 [Просмотр аспектов управления на основе политик в объекте SQL Server](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Копирование состояния аспекта управления на основе политик в XML-файл](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](administer-servers-by-using-policy-based-management.md)  
  
  
