---
title: Простой XML-код Образец входного файла (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 5b00e4eb-1742-43ec-98d8-d84216b6b840
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 67e18d1be6061dca4e2dd963a359e515ac725b3b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733463"
---
# <a name="simple-xml-input-file-sample-dta"></a>Образец простого входного файла XML (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Скопируйте и вставьте этот образец простого входного файла XML, используемого для настройки рабочих нагрузок, в любой текстовый или XML-редактор. Затем замените значения, заданные для элементов **Server**, **Database**, **Schema**, **Table**, **Workload**и **TuningOptions** , значениями для конкретного сеанса настройки. Дополнительные сведения об атрибутах и дочерних элементах, которые могут использоваться с этими элементами, см. в разделе [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md). В следующем образце используется только подмножество доступных атрибутов и параметров дочерних элементов.  
  
## <a name="code"></a>Код  
 [!code-xml[InputFileSamples#SimpleXMLInputFile](../../tools/dta/codesnippet/xml/simple-xml-input-file-sa_1.xml)]  
  
## <a name="see-also"></a>См. также:  
 [Запуск и использование помощника по настройке ядра СУБД](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)   
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
