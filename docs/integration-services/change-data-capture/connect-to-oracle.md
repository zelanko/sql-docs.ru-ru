---
title: Соединение с Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9be5e4b3652dec337583123e0232ce9b1442af73
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924008"
---
# <a name="connect-to-oracle"></a>Соединение с Oracle

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  При первом добавлении или изменении таблиц, используемых на экземпляре CDC, программа может попросить установить соединение с базой данных Oracle. Необходимо ввести учетные данные пользователя Oracle, который имеет доступ к схеме отслеживаемых таблиц. Введите в этом диалоговом окне следующие данные:  
  
 **Аутентификация**  
  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows**. Выберите этот параметр, чтобы использовать учетные данные текущего пользователя Windows. Этот параметр можно использовать только в том случае, если в базе данных Oracle настроено использование проверки подлинности Windows.  
  
-   **Проверка подлинности Oracle**. При выборе этого варианта необходимо ввести **Имя пользователя** и **Пароль** пользователя в базе данных Oracle, с которой устанавливается соединение.  
  
## <a name="see-also"></a>См. также:  
 [Добавление таблиц в экземпляр CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  
