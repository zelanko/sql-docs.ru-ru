---
title: Загрузка по порядковому номеру | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fdc7728fe06df708efd973423f5c8c05333ce189
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041599"
---
# <a name="loading-by-ordinal"></a>Загрузка по порядковому номеру
В ODBC *2.x*, чтобы повысить производительность процесса подключения может быть выполнена загрузка по порядковому номеру. ODBC *2.x* драйвер экспортирует функцию фиктивный с 199 порядкового номера; когда диспетчер драйверов обнаруживает его, он разрешает адресов функций ODBC, по порядковому номеру, а не по имени. Эта функция по-прежнему поддерживается для ODBC *2.x* драйверов, но не поддерживается для ODBC *3.x* драйверы.
