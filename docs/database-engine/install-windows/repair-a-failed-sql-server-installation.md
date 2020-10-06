---
description: Исправление неудавшейся установки SQL Server
title: Исправление неудавшейся установки SQL Server | Microsoft Docs
deescription: This article describes the scenarios where you can try a repair operation to fix failed SQL Server installation.
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 90c11b28-892b-44d6-978e-0eee48c75b7d
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 91c7f3a0ef51b752b2c1460578319929f7ae4113
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671004"
---
# <a name="repair-a-failed-sql-server-installation"></a>Исправление неудавшейся установки SQL Server

[!INCLUDE [SQL Server -Windows Only](../../includes/applies-to-version/sql-windows-only.md)]

Операцию исправления можно применять в следующих случаях.  
  
- Для исправления экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который оказался поврежденным после успешной установки. 
  
- Для исправления экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если операция обновления была отменена или завершилась ошибкой после сопоставления имени экземпляра с экземпляром после обновления. 
  
    - Если в сводном журнале присутствует следующее сообщение, экземпляр можно исправить после ошибки обновления:  
  
         «Не удалось обновить[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы продолжить, определите причину сбоя, устраните проблему, а затем запустите исправление установки».  
  
    - Если в сводном журнале присутствует следующее сообщение, необходимо удалить и повторно установить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Исправить экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] невозможно. 
  
         «Не удалось обновить[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы продолжить, определите причину сбоя и устраните проблему».  
  
 В ходе восстановления экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполняются следующие действия.  
  
- Заменяются все отсутствующие или поврежденные файлы. 
  
- Заменяются все отсутствующие или поврежденные разделы реестра. 
  
- Для всех отсутствующих или недопустимых параметров конфигурации устанавливаются значения по умолчанию. 
  
 Перед тем как продолжить, при использовании отказоустойчивых кластеров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ознакомьтесь со следующими важными сведениями.  
  
- Исправление должно быть запущено на отдельных узлах кластера. 
  
- Для исправления узла отказоустойчивого кластера после неудачной операции «Подготовка» используйте кнопку **Удалить узел** , а затем еще раз осуществите шаг «Подготовка». Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md). 
  
## <a name="repair-a-failed-installation-of-ssnoversion-from-the-installation-center"></a>Исправление неудавшейся установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в центре установки 
  
1. Запустите программу установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (setup.exe), расположенную на установочном носителе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 
  
2. После выполнения необходимых условий и проверки системы программа установки выводит страницу центра установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . 
  
3. Для начала операции исправления нажмите кнопку **Обслуживание** в левой части области навигации, а затем кнопку **Исправление** . 
  
   >[!TIP]  
   > Если центр установки был запущен из меню «Пуск», то в этот раз потребуется указать расположение установочного носителя. 
  
4. Будут запущены правило поддержки установки и файлы подпрограмм, чтобы удостовериться, что в системе установлены необходимые компоненты и что компьютер отвечает правилам проверки. Для продолжения нажмите кнопку **ОК** или **Установить** . 
  
5. На странице Выбор экземпляра выберите экземпляр для исправления и нажмите кнопку **Далее** , чтобы продолжить. 
  
6. Будут запущены правила исправления для проверки операции. Чтобы продолжить, нажмите кнопку **Далее**. 
  
7. Страница «Готовность к исправлению» показывает, что операция готова к продолжению. Чтобы продолжить, нажмите кнопку **Исправить**. 
  
8. Страница «Состояние исправления» показывает состояние операции исправления. Страница «Готово» показывает, что операция завершена. 
  
### <a name="to-repair-a-failed-installation-of-ssnoversion-using-command-prompt"></a>Исправление ошибочной установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из командной строки  
  
1. Выполните в командной строке следующую команду:  
  
    ```  
    Setup.exe /q /ACTION=Repair /INSTANCENAME=instancename  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [Инструкции по установке](/previous-versions/sql/)  
  
