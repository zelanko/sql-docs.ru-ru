---
title: Установка быстрого анализа | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 94f4fe123cb37e60e175ad39b932e61376e217b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096454"
---
# <a name="set-fast-parse"></a>Установка быстрого анализа
  Свойство быстрого анализа необходимо установить для каждого столбца источника или преобразования, использующего этот анализ. Для установки этого свойства используется расширенный редактор источника «Неструктурированный файл» и преобразование «Преобразование данных».  
  
### <a name="to-set-fast-parse"></a>Установка быстрого анализа  
  
1.  Щелкните правой кнопкой источник "Неструктурированный файл" или преобразование "Преобразование данных" и выберите **Показать расширенный редактор**.  
  
2.  В диалоговом окне **Расширенный редактор** перейдите на вкладку **Свойства входов и выходов** .  
  
3.  На панели **Входы и выходы** щелкните столбец, для которого нужно включить быстрый анализ.  
  
4.  В окне «Свойства» разверните **Custom Properties** узел, а затем задайте `FastParse` свойства `True`.  
  
5.  Нажмите кнопку **ОК**.  
  
  