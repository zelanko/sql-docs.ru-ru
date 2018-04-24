---
title: Настройка брандмауэра для доступа к FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: blob
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b3d349e80f7d422f0cbf51336b3d10b42aaa595
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="configure-a-firewall-for-filestream-access"></a>Настройка брандмауэра для доступа FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Чтобы использовать FILESTREAM в среде, защищенной брандмауэром, как клиент, так и сервер должны быть в состоянии разрешать имена DNS для сервера, содержащего файлы FILESTREAM. Для данных FILESTREAM требуется, чтобы были открыты порты 139 и 445 для общего доступа к файлам Windows.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>Открытие портов общего доступа к файлам Windows на компьютере под управлением Windows 7  
  
1.  На панели управления откройте элемент **Брандмауэр Windows**.  
  
2.  На левой панели нажмите кнопку **Дополнительные параметры**. Если появится запрос пароля администратора или подтверждения, введите пароль или подтверждение.  
  
3.  На левой панели окна **Брандмауэр Windows в режиме повышенной безопасности** щелкните раздел **Правила для входящих подключений**, затем на правой панели выберите пункт **Создать правило**.  
  
4.  Чтобы добавить TCP-порт 139, следуйте инструкциям мастера создания правила для нового входящего подключения.  
  
5.  Повторите предыдущий шаг для добавления TCP-порта 445.  
  
6.  Закройте диалоговое окно **Брандмауэр Windows в режиме повышенной безопасности** .  
  
  
