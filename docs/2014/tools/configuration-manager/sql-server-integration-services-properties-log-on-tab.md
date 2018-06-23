---
title: Свойства служб SQL Server Integration Services (вкладка "Вход в систему") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2d46a9e86aaa261f32a0aab2c49891d8fc195a4e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193716"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a>Свойства служб SQL Server Integration Services (вкладка «Вход в систему»)
  Используйте вкладку **Вход** в диалоговом окне [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Свойства** для указания учетной записи, используемой службой [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , а также для запуска и остановки службы.  
  
## <a name="options"></a>Параметры  
 **Локальная системная учетная запись**  
 Укажите локальную системную учетную запись, для которой не требуется пароль. Однако локальная системная учетная запись может ограничить взаимодействие служб с другими серверами, это зависит от прав доступа, предоставленных этой учетной записи.  
  
 **Эта учетная запись**  
 Укажите локальную или доменную учетную запись пользователя, использующую проверку подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует использовать доменную учетную запись пользователя с минимальными правами. Дополнительные сведения о выборе учетной записи см. в разделе «Настройка учетных записей служб Windows» электронной документации.  
  
 **Имя учетной записи**  
 Укажите имя локальной или доменной учетной записи.  
  
 **Пароль**  
 Введите пароль для учетной записи.  
  
 **Подтверждение пароля**  
 Введите пароль для учетной записи еще раз.  
  
 **Запуск**  
 Запускает службу.  
  
 **Остановить**  
 Остановить службу.  
  
 **Приостановить**  
 Приостановить службу.  
  
 **Возобновить**  
 Возобновить приостановленную работу службы.  
  
  