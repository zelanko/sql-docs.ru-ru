---
title: Настройка IntelliSense (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Options [SQL Server Management Studio], IntelliSense
- modifying IntelliSense options
- IntelliSense [SQL Server], modifying options
ms.assetid: 3ffc9f31-4efa-4c1a-a033-ed1dc48b065f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8c2d84b09b0026f13ccae0f71696b84da56d8721
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842612"
---
# <a name="configure-intellisense-sql-server-management-studio"></a>Настройка IntelliSense (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Большинство параметров технологии [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense по умолчанию включено. Отдельные параметры IntelliSense можно отключить и вместо этого выполнять соответствующие действия посредством команды меню или сочетания клавиш.  
  
> [!IMPORTANT]  
>  Некоторые изменения вступают в силу только после перезапуска редактора.  Чтобы увидеть изменения, откройте новый сеанс редактора Transact-SQL.
  
### <a name="to-turn-statement-completion-options-off-by-default"></a>Чтобы отключить параметры заполнения инструкций по умолчанию  

> [!NOTE]
> Хранилище данных SQL не поддерживает IntelliSense.
>
>
  
1.  В меню **Сервис** выберите команду **Параметры**.  
  
2.  Раскройте список **Редактор текстов**, затем список **Все языки**, **Transact-SQL**или **XML**, после чего выберите пункт **Общие**.  
  
3.  Снимите флажки параметров заполнения инструкций, которые не требуются, а затем нажмите кнопку **ОК**.  
  
### <a name="to-modify-transact-sql-intellisense-options"></a>Изменение параметров технологии Transact-SQL IntelliSense  
  
1.  В меню **Сервис** выберите команду **Параметры**.  
  
2.  Раскройте список **Текстовый редактор**, затем список **Transact-SQL**, после чего выберите **IntelliSense**.  
  
3.  Снимите флажки параметров IntelliSense, которые не требуются.  
  
4.  Чтобы изменить размер скрипта, при котором отключаются функции IntelliSense, выберите размер из списка **Максимальный размер скрипта** .  
  
5.  Чтобы изменить правила учета регистра, применяемые к именам функций в списках завершения, выберите спецификацию регистра в списке **Регистр для имен встроенных функций** .  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
