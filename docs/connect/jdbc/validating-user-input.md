---
description: Проверка вводимых пользователем данных
title: Проверка данных, введенных пользователем | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cbe5ef27b46481eeb32478eaee9866a73ce11802
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450116"
---
# <a name="validating-user-input"></a>Проверка вводимых пользователем данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

При создании приложения, которое получает доступ к данным, следует исходить из того, что все данные, вводимые пользователем, являются вредоносными, пока обратное не доказано. В противном случае приложение окажется уязвимым для атак. Один из возможных типов атак — это внедрение кода SQL. При атаке такого рода вредоносный код добавляется в строки, передаваемые на анализ и выполнение в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы избежать этого типа атаки, следует по возможности использовать хранимые процедуры с параметрами и всегда проверять вводимые данные.

Проверка вводимых пользователем данных в клиентском коде позволяет сократить количество ненужных циклов приема-передачи данных на сервер. Проверка параметров для хранимых процедур на сервере также важна для выявления вводимых данных, недопустимость которых не была обнаружена на стороне клиента.

Дополнительные сведения об атаке путем внедрения кода SQL и о том, как ее избежать, см. в соответствующем разделе электронной документации на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о проверке параметров хранимых процедур см. в разделе о хранимых процедурах ([!INCLUDE[ssDE](../../includes/ssde_md.md)]) и связанных разделах электронной документации на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a>См. также раздел

[Защита приложений JDBC Driver](../../connect/jdbc/securing-jdbc-driver-applications.md)
