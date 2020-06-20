---
title: Программа sqlps | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
author: stevestein
ms.author: sstein
ms.openlocfilehash: bcce5bcbab747e9febb1ab3ac8de662a8d3974a4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85006923"
---
# <a name="sqlps-utility"></a>программа sqlps
  Программа `sqlps` запускает сеанс Windows PowerShell 2.0 с помощью поставщика [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell, а также загруженных и зарегистрированных командлетов. Можно вводить команды или скрипты PowerShell, в которых используются компоненты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell для работы с экземплярами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и их объектами.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте модуль `sqlps` PowerShell. Дополнительные сведения о `sqlps` модуле см. в разделе [Импорт модуля sqlps](../database-engine/import-the-sqlps-module.md).  
  
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
 Указывает, что `sqlps` выходные данные служебной программы должны быть форматированы как текстовые строки (**текст**) или в сериализованном формате CLIXML (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Указывает, что входные данные для `sqlps` служебной программы форматируются как текстовые строки (**текст**) или в сериализованном формате CLIXML (**XML**).  
  
 **-Command**  
 Указывает команду для запуска программой `sqlps`. `sqlps`Программа выполняет команду, а затем завершает работу, если не задан параметр **-Exit** . После параметра **-Command**не следует указывать какие-либо иные параметры, так как они будут интерпретироваться как параметры команды.  
  
 **-**  
 **-Command —** указывает, что `sqlps` Программа считывает входные данные из стандартного ввода.  
  
 *script_block* [ **-args**_argument_array_ ]  
 Указывает блок команд PowerShell для выполнения, который должен быть заключен в фигурные скобки: {}. *Script_block* можно указать только при `sqlps` вызове служебной программы из **PowerShell** или из другого `sqlps` сеанса программы. Параметр *массив_аргументов* представляет собой массив переменных PowerShell, содержащий аргументы для команд PowerShell из параметра *блок_скрипта*.  
  
 *string* [ *параметры_команды* ]  
 Указывает строку, содержащую команды PowerShell для запуска. Используйте формат **"& { *`command`* }"**. Кавычки обозначают строку, а оператор Invoke (&) заставляет `sqlps` программу выполнить команду.  
  
 [ **-?** |  **-Help** ]  
 Показывает синтаксис параметров программы `sqlps`.  
  
## <a name="remarks"></a>Remarks  
 `sqlps`Программа запускает среду PowerShell (PowerShell.exe) и загружает [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] модуль PowerShell. Модуль, также именуемый `sqlps` , загружает и регистрирует следующие [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] оснастки PowerShell:  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Реализует поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell и связанные с ним командлеты, такие как **Encode-SqlName** и **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Реализует командлеты **Invoke-Sqlcmd** и **Invoke-PolicyEvaluation** .  
  
 С помощью программы `sqlps` можно делать следующее.  
  
-   Вводить команды PowerShell в интерактивном режиме.  
  
-   Запускать файлы скриптов PowerShell.  
  
-   Запускать командлеты служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Использовать пути поставщика служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для передвижения по иерархии объектов среды служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 По умолчанию `sqlps` программа запускается с политикой выполнения скриптов, для которой задано значение " **ограничено**". Это предотвращает запуск любых скриптов PowerShell. Командлет **Set-ExecutionPolicy** обеспечивает возможность запуска как подписанных, так и любых других скриптов. Запускать следует только скрипты из надежных источников, а также рекомендуется защитить все входные и выходные файлы соответствующими разрешениями NTFS. Дополнительные сведения о включении скриптов PowerShell см. в разделе [Запуск скриптов Windows PowerShell](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/).  
  
 Версия программы `sqlps` в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] и [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] была реализована как мини-оболочка Windows PowerShell 1.0. Мини-оболочки имеют определенные ограничения, такие как запрет на загрузку пользователями других оснасток, помимо загруженных мини-оболочкой. Эти ограничения не относятся к [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] и более поздним версиям программы, где изменилось использование модуля `sqlps`.  
  
## <a name="examples"></a>Примеры  

### <a name="a-run-the-sqlps-utility-in-default-interactive-mode-without-the-copyright-banner"></a>A. Запуск служебной программы sqlps в режиме по умолчанию (интерактивном) без баннера со сведениями об авторских правах
  
```cmd
sqlps -NoLogo  
```  
  
### <a name="b-run-a-sql-server-powershell-script-from-the-command-prompt"></a>Б. Запуск скрипта SQL Server PowerShell из командной строки
  
```cmd
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
### <a name="c-run-a-sql-server-powershell-script-from-the-command-prompt-and-keep-running-after-the-script-completes"></a>В. Запуск скрипта SQL Server PowerShell из командной строки с продолжением выполнения после завершения скрипта
  
```cmd
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>См. также:  
 [Включение или отключение сетевого протокола сервера](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
