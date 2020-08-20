---
description: Применение правил качества данных к источнику данных
title: Применение правил качества данных к источнику данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58e6e75f520bcd966cf2b1ae8e2edbc0f7a568f7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484433"
---
# <a name="apply-data-quality-rules-to-data-source"></a>Применение правил качества данных к источнику данных

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Можно использовать службы Data Quality Services (DQS) для корректировки данных в потоке данных пакета, подключив преобразование DQS Cleansing к источнику данных. Дополнительные сведения о языке DQS см. в разделе [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Дополнительные сведения об этом преобразовании см. в разделе [DQS Cleansing Transformation](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 При обработке данных с помощью преобразования DQS Cleansing, создается проект служб DQS на сервере служб DQS. Для управления проектом используется клиент DQS. Дополнительные сведения см. в статье [Открытие, разблокировка, переименование и удаление проекта качества данных](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Исправление данных в потоке данных  
  
1.  Создайте пакет.  
  
2.  Добавьте и настройте преобразование «Очистка DQS». Дополнительные сведения см. в разделе [DQS Cleansing Transformation Editor Dialog Box](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Соедините преобразование «Очистка DQS» с источником данных.  
  
  
