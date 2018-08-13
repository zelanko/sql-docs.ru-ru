---
title: Проверка вводимых пользователем данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2320ed83c095d460aa233ac0227f37c15eca88b
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662316"
---
# <a name="validating-user-input"></a>Проверка введенного пользователем

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

При создании приложения, которое получает доступ к данным, следует исходить из того, что все данные, вводимые пользователем, являются вредоносными, пока обратное не доказано. В противном случае приложение окажется уязвимым для атак. Один из возможных типов атак — это внедрение кода SQL. При атаке такого рода вредоносный код добавляется в строки, передаваемые на анализ и выполнение в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Чтобы избежать этого типа атаки, следует по возможности использовать хранимые процедуры с параметрами и всегда проверять вводимые данные.

Проверка вводимых пользователем данных в клиентском коде позволяет сократить количество ненужных циклов приема-передачи данных на сервер. Проверка параметров для хранимых процедур на сервере также важна для выявления вводимых данных, недопустимость которых не была обнаружена на стороне клиента.

Дополнительные сведения об атаке путем внедрения кода SQL и о том, как ее избежать, см. в соответствующем разделе электронной документации на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения о проверке параметров хранимых процедур см. в разделе "Хранимые процедуры ([!INCLUDE[ssDE](../../includes/ssde_md.md)])" и связанных разделах электронной документации на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].

## <a name="see-also"></a>См. также:

[Защита приложений драйвера JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)
