---
title: Программа sqlps | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
caps.latest.revision: 20
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: b49895ee08de2a9f08d263c92f5372c6b22ec604
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097663"
---
# <a name="sqlps-utility"></a>программа sqlps
  Программа `sqlps` запускает сеанс Windows PowerShell 2.0 с помощью поставщика [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell, а также загруженных и зарегистрированных командлетов. Можно вводить команды или скрипты PowerShell, в которых используются компоненты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell для работы с экземплярами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и их объектами.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте модуль `sqlps` PowerShell. Дополнительные сведения о `sqlps` модуля, в разделе [импорта модуля SQLPS](../database-engine/import-the-sqlps-module.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -argsargument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **-NoLogo**  
 Указывает, что программа `sqlps` не должна отображать баннер со сведениями об авторских правах при запуске.  
  
 **-NoExit**  
 Указывает, что программа `sqlps` должна продолжать выполняться после выполнения команд запуска.  
  
 **-NoProfile**  
 Указывает программе `sqlps` не загружать профиль пользователя. В профилях пользователей записываются часто используемые псевдонимы, функции и переменные для использования в различных сеансах PowerShell.  
  
 **-OutPutFormat** { **Text** | **XML** }  
 Указывает, что `sqlps` выходные данные программы отформатированы в виде текстовых строк (**текст**), либо в сериализованном формате CLIXML (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Указывает, что вход `sqlps` программа форматируется в виде текстовых строк (**текст**), либо в сериализованном формате CLIXML (**XML**).  
  
 **-Command**  
 Указывает команду для запуска программой `sqlps`. `sqlps` Служебная программа запускает команду, а затем завершает работу, если не **- NoExit** также указан. После параметра **-Command**не следует указывать какие-либо иные параметры, так как они будут интерпретироваться как параметры команды.  
  
 **-**  
 **-Команда -** указывает, что `sqlps` программа считывает входные данные из стандартного ввода.  
  
 *блок_сценария* [ **-args***массив_аргументов* ]  
 Указывает блок команд PowerShell для выполнения, который должен быть заключен в фигурные скобки: {}. *Блок_скрипта* можно указывать только в случае `sqlps` вызова служебной программы из любой **PowerShell** или другой `sqlps` сеанса служебной программы. Параметр *массив_аргументов* представляет собой массив переменных PowerShell, содержащий аргументы для команд PowerShell из параметра *блок_скрипта*.  
  
 *string* [ *параметры_команды* ]  
 Указывает строку, содержащую команды PowerShell для запуска. Используйте формат **«& {*`command`*}»**. Кавычки определяют строку, а оператор вызова (&) указывает программе `sqlps` запустить команду.  
  
 [ **-?** | **-Help** ]  
 Показывает синтаксис параметров программы `sqlps`.  
  
## <a name="remarks"></a>Примечания  
 `sqlps` Запускает среду PowerShell (PowerShell.exe) и загружает [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] модуля PowerShell. Модуль, также именуемый `sqlps`, загружает и регистрирует следующие [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] оснастки PowerShell:  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Реализует поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell и связанные с ним командлеты, такие как **Encode-SqlName** и **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Реализует командлеты **Invoke-Sqlcmd** и **Invoke-PolicyEvaluation** .  
  
 С помощью программы `sqlps` можно делать следующее.  
  
-   Вводить команды PowerShell в интерактивном режиме.  
  
-   Запускать файлы скриптов PowerShell.  
  
-   Запускать командлеты служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Использовать пути поставщика служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для передвижения по иерархии объектов среды служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 По умолчанию `sqlps` программа запускается с политикой выполнения сценариев **Restricted**. Это предотвращает запуск любых скриптов PowerShell. Командлет **Set-ExecutionPolicy** обеспечивает возможность запуска как подписанных, так и любых других скриптов. Запускать следует только скрипты из надежных источников, а также рекомендуется защитить все входные и выходные файлы соответствующими разрешениями NTFS. Дополнительные сведения о включении скриптов PowerShell см. в разделе [Запуск скриптов Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=103166).  
  
 Версия `sqlps` служебной программы в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] и [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] была реализована как мини-оболочка Windows PowerShell 1.0. Мини-оболочки имеют определенные ограничения, такие как запрет на загрузку пользователями других оснасток, помимо загруженных мини-оболочкой. Эти ограничения не относятся к [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] и более поздним версиям программы, где изменилось использование модуля `sqlps`.  
  
## <a name="examples"></a>Примеры  
 **А. Запуск служебной программы sqlps в режиме по умолчанию (интерактивном) без баннера со сведениями об авторских правах**  
  
```  
sqlps -NoLogo  
```  
  
 **Б. Запуск сценария SQL Server PowerShell из командной строки**  
  
```  
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
 **В. Запуск сценария SQL Server PowerShell из командной строки с продолжением выполнения после завершения сценария**  
  
```  
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>См. также  
 [Включение или отключение сетевого протокола сервера](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
  
  