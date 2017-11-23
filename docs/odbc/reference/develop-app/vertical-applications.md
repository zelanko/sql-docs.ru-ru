---
title: "Вертикальные приложения | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce78adb6af76ff17b6df0e0ecc910f1266bf7dea
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="vertical-applications"></a>Вертикальные приложения
Вертикальные приложения обычно выполняются от одного СУБД, четко определенную задачу. Например приложение для регистрации заказов отслеживает заказы в компании. Что общих у этих типов приложений, что схемы базы данных обычно создаются разработчиком приложения и, хотя приложение может работать с количеством различных DBMS, она работает с одной СУБД для одного клиента.  
  
 Поскольку вертикальные приложения обычно требуется режим работы некоторых функций, таких как Прокручиваемые курсоры и транзакции, они редко поддерживают все СУБД. Вместо этого они обычно бывают возможность взаимодействия между ограниченный набор СУБД. Как правило разработчики приложений вертикальной выбрать поддержку этих СУБД, которые представляют большой доли рынка, а остальные пропускались. Они могут даже поддерживать по выбору специальных драйверов для этих СУБД для уменьшения их тестирование и затраты на поддержку продукта.  
  
 Так как вертикальные приложения могут использовать набор известных СУБД, иногда они содержат драйвер конкретных СУБД или кода. Тем не менее такой код лучше всего сведена к минимуму, поскольку для нее требуется дополнительное время для обслуживания.
