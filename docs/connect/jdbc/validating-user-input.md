---
title: Проверка пользовательского ввода | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2bda7891ae7ec7c64053e0c586a05e54b4cc4634
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="validating-user-input"></a>Проверка введенного пользователем
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При создании приложения, которое получает доступ к данным, следует исходить из того, что все данные, вводимые пользователем, являются вредоносными, пока обратное не доказано. В противном случае приложение окажется уязвимым для атак. Один тип атаке такого рода вызывается путем внедрения кода SQL, где вредоносный код добавляется в строки, передающиеся затем в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для синтаксического анализа и выполнения. Чтобы избежать этого типа атаки, следует по возможности использовать хранимые процедуры с параметрами и всегда проверять вводимые данные.  
  
 Проверка вводимых пользователем данных в клиентском коде позволяет сократить количество ненужных циклов приема-передачи данных на сервер. Проверка параметров для хранимых процедур на сервере также важна для выявления вводимых данных, недопустимость которых не была обнаружена на стороне клиента.  
  
 Дополнительные сведения о путем внедрения кода SQL и способах ее устранения см. в разделе «Инъекция SQL» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации. Дополнительные сведения о проверке параметров хранимых процедур см. в разделе «хранимые процедуры ([!INCLUDE[ssDE](../../includes/ssde_md.md)])» и в связанных разделах [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="see-also"></a>См. также  
 [Защита приложений драйвера JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
