---
title: Загрузка по Ординаль Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64bff8dcdd3802f75dc402c9ada60f82580aca5c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288724"
---
# <a name="loading-by-ordinal"></a>Загрузка по порядковому номеру
В ODBC *2.x*, загрузка по ординатору может быть выполнена для повышения производительности процесса соединения. Водитель ODBC *2.x* экспортирует фиктивную функцию с ординатором 199; когда менеджер драйвера обнаруживает его, он решает адреса функций ODBC по илиистому, а не по имени. Эта функция по-прежнему поддерживается для драйверов ODBC *2.x,* но не поддерживается для драйверов ODBC *3.x.*
