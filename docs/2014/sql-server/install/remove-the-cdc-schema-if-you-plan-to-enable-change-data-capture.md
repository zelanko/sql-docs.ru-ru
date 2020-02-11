---
title: Удалите схему CDC, если планируется включить систему отслеживания измененных данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cc580a6032a19eb8248759669278f8730fc617cb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66092951"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>Удаление схемы cdc, если планируется ввести в действие систему отслеживания измененных данных
  База данных уже содержит схему cdc. Если планируется разрешить использование системы отслеживания измененных данных после обновления, необходимо вначале удалить эту схему cdc. Если в базе данных включено применение системы отслеживания измененных данных, то в [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] создается новая схема с именем cdc.  
  
  
