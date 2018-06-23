---
title: Выбор способа импорта данных (службы SSAS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.choosehowtoimpdata.f1
ms.assetid: 17dc6903-c239-46aa-a3b0-6e3156accacc
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9929f61537fdf635ffd130b75d9e2738be256aab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194151"
---
# <a name="choose-how-to-import-the-data-ssas"></a>Выбор способа импорта данных (SSAS)
  На этой странице **мастера импорта таблиц** можно выбрать порядок импорта данных из выбранного источника данных. Для доступа к мастеру из [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Выберите из списка таблиц и представлений, чтобы выбрать данные для импорта**  
 Выберите этот параметр, если необходимо импортировать данные посредством выбора из списка.  
  
> [!NOTE]  
>  Этот параметр доступен, только если выбранный источник данных предоставляет сведения о схеме, поддерживаемые **мастером импорта таблиц** .  
  
 **Написать запрос, указывающий данные для импорта**  
 Выберите этот параметр, если необходимо импортировать данные с помощью SQL-запроса. С помощью SQL-запроса можно управлять импортируемыми данными. Например, можно объединить данные из различных таблиц или выбрать только строки, отвечающие определенным критериям.  
  
  