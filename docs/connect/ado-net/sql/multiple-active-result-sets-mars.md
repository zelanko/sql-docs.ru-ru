---
title: Режим MARS
description: Сведения о том, как можно открыть несколько экземпляров SqlDataReader в одном подключении, где каждый экземпляр SqlDataReader запускается отдельной командой.
ms.date: 08/15/2019
ms.assetid: c90ef863-bac7-44cf-adc1-f05c36fcf57d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 4475e4b8a71b4abcf4e1c2324a49e03a8bb64fbb
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896669"
---
# <a name="multiple-active-result-sets-mars"></a>Режим MARS

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Режим MARS — это новая функция, которая позволяет выполнять несколько пакетов в одном подключении. В предыдущих версиях можно было в любой момент выполнять только один пакет для каждого подключения. Выполнение нескольких пакетов с режимом MARS не подразумевает одновременное выполнение операций.  
  
## <a name="in-this-section"></a>В этом разделе  
[Включение нескольких активных результирующих наборов](enable-multiple-active-result-sets.md)  
Приведено описание того, как использовать MARS в SQL Server.  
  
[Манипулирование данными](manipulate-data.md)  
Содержит примеры программирования приложений для MARS.  
  
## <a name="related-sections"></a>См. также  
[Асинхронные операции](asynchronous-operations.md)  
Содержит сведения об использовании новых асинхронных функций в .NET.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
