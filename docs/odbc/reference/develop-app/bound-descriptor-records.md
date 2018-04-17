---
title: Привязать дескриптор записи | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bound descriptor records [ODBC]
- descriptors [ODBC], bound descriptor records
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1e7c9c3d93403515c118757a6a947a6b5a68b9c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bound-descriptor-records"></a>Связанный дескриптор записи
Когда приложение задает поле записи дескриптора SQL_DESC_DATA_PTR, чтобы он больше не содержит значение null, запись считается *привязан*.  
  
 Если дескриптор является APD, каждой присоединенной записи составляет связанного параметра. Для входных параметров приложения необходимо привязать для каждого маркера параметра динамического параметра в инструкции SQL до выполнения инструкции. Для выходных параметров приложения не требуется привязать параметр.  
  
 Если дескриптор является Отменить, описывающий строку базы данных каждой присоединенной записи составляет связанного столбца.
