---
title: Привязать дескриптор записи | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ac161220673c32f13c08ab7588c269237b5aa6f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907575"
---
# <a name="bound-descriptor-records"></a>Связанный дескриптор записи
Когда приложение задает поле записи дескриптора SQL_DESC_DATA_PTR, чтобы он больше не содержит значение null, запись считается *привязан*.  
  
 Если дескриптор является APD, каждой присоединенной записи составляет связанного параметра. Для входных параметров приложения необходимо привязать для каждого маркера параметра динамического параметра в инструкции SQL до выполнения инструкции. Для выходных параметров приложения не требуется привязать параметр.  
  
 Если дескриптор является Отменить, описывающий строку базы данных каждой присоединенной записи составляет связанного столбца.
