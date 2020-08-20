---
description: Как просмотреть свойства экземпляра CDC
title: Как просмотреть свойства экземпляра CDC | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bce9b82-7bbd-41df-b3f4-4b40b8bad474
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 670f64d956c8b8b7df281c66598a79a38ed7ef2f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88496160"
---
# <a name="how-to-view-the-cdc-instance-properties"></a>Как просмотреть свойства экземпляра CDC

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Эта процедура описывает использование консоли конструктора CDC для просмотра сведений об экземплярах, создаваемых для поддержки управления работой экземпляров.  
  
### <a name="to-view-information-about-a-specific-instance"></a>Просмотр сведений об определенном экземпляре  
  
1.  В меню **Пуск** выберите **Консоль конструктора CDC**.  
  
2.  На панели слева разверните узел **Отслеживание измененных данных** , а затем разверните службу, содержащую экземпляр, данные которого необходимо просмотреть.  
  
3.  Выберите имя нужного экземпляра.  
  
     Сведения об экземпляре будут отображены в центральной части консоли конструктора CDC. Сведения разделены на четыре вкладки. Все вкладки доступны только для чтения.  
  
     **Состояние**  
     На этой вкладке отображаются сведения о текущем состоянии отслеживания измененных данных для экземпляра. Сведения о том, что отображено на этой вкладке, приведены в пункте **Вкладки средства просмотра** раздела [Manage a CDC Instance](../../integration-services/change-data-capture/manage-a-cdc-instance.md).  
  
     **Oracle**  
     На этой вкладке отображаются общие сведения об экземпляре CDC и базе данных-источнике Oracle. Сведения о том, что отображено на этой вкладке, приведены в разделе [Edit the Oracle Database Properties](../../integration-services/change-data-capture/edit-the-oracle-database-properties.md).  
  
     **Таблицы**  
     На этой вкладке отображаются сведения о таблицах, включенных в отслеживание измененных данных. На ней также указаны столбцы, состояние которых отслеживается. Сведения о том, что отображено на этой вкладке, приведены в разделе [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
     **Дополнительно**  
     На этой вкладке приведен список дополнительных свойств, которые задаются в редакторе свойств. Сведения о том, что отображено на этой вкладке, приведены в разделе [Edit the Advanced Properties](../../integration-services/change-data-capture/edit-the-advanced-properties.md).  
  
  
