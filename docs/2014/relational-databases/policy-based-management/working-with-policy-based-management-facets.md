---
title: Работа с аспектами управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
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
ms.openlocfilehash: 037eb57f53bf583195efdf1f91fcd55f94ebaddc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676901"
---
# <a name="working-with-policy-based-management-facets"></a>Работа с аспектами управления на основе политик
  Аспект управления на основе политик — это ряд логических свойств, которые связаны с определенной областью, представляющей интерес с точки зрения управления. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает несколько стандартных аспектов. Например, средство настройки контактной зоны, определяющее функции, отключенные по умолчанию.  
  
 При управлении несколькими похожими средами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить аспект в одном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], скопировать состояние аспекта в файл и импортировать этот файл на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве политики. При преобразовании состояния в политику она может быть применена к другим экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], объектам экземпляров, базам данных или объектам баз данных.  
  
 Этот раздел описывает способ копирования состояния аспекта в XML-файл.  
  
##  <a name="BeforeYouBegin"></a> Permissions  
 Для процедуры в этом разделе требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="viewing-and-copying-facet-states"></a>Просмотр и копирование состояний аспекта  
 [Просмотр аспектов управления на основе политик в объекте SQL Server](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Копирование состояния аспекта управления на основе политик в XML-файл](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](administer-servers-by-using-policy-based-management.md)  
  
  
