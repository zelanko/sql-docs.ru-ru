---
title: Параметры (текстовый редактор — Transact-SQL-IntelliSense) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Advanced
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Advanced
dev_langs:
- TSQL
ms.assetid: 1855d916-5bf9-4d94-b0fb-9f9bb05ff950
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b39d0ad9439e265b80bdfc408389332fe308848e
ms.sourcegitcommit: 4b5919e3ae5e252f8d6422e8e6fddac1319075a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2020
ms.locfileid: "83000661"
---
# <a name="options-text-editor-transact-sql-intellisense"></a>Параметры (текстовый редактор — Transact-SQL-IntelliSense)
  Диалоговое окно **Параметры** позволяет изменять параметры технологии IntelliSense для редактора запросов [!INCLUDE[ssDE](../includes/ssde-md.md)] . Для доступа к этим параметрам в меню **Сервис** выберите пункт **Параметры**, разверните папку **Редактор текстов**, раскройте папку **Transact-SQL** и нажмите кнопку **Дополнительно**.  
  
## <a name="transact-sql-intellisense-settings"></a>Параметры технологии IntelliSense для Transact-SQL  
 Указывает параметры технологии IntelliSense для редактора запросов [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
### <a name="enable-intellisense"></a>Включение технологии IntelliSense  
 Включает функции технологии IntelliSense. Если этот флажок не установлен, то определенные параметры технологии IntelliSense недоступны. По умолчанию этот флажок установлен.  
  
 **Подчеркивать ошибки**  
 Обнаруживает синтаксические и семантические ошибки в инструкциях [!INCLUDE[tsql](../includes/tsql-md.md)] в окне запроса. Все ошибки и предупреждения показаны красным цветом. Ошибки и предупреждения поддерживаются только для инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] , для которых реализована технология IntelliSense. По умолчанию этот флажок установлен.  
  
 **Определить структуру инструкций**  
 Включает функцию структурирования при открытии файла. В результате создаются свертываемые блоки кода [!INCLUDE[tsql](../includes/tsql-md.md)] . По умолчанию этот флажок установлен.  
  
 **Максимальный размер скрипта**  
 Определяет размер, при котором отключается функциональность технологии IntelliSense. Если скрипт превышает указанный размер, выдается предупреждение. Все функции технологии IntelliSense, за исключением выделения цветом, отключаются для этого окна редактора. Технология IntelliSense повторно активируется, если удалить достаточный фрагмент текста, чтобы уменьшить размер скрипта до допустимого. Включение технологии IntelliSense для крупных скриптов может привести к снижению производительности медленных компьютеров. Допустимые размеры 100 КБ, 500 КБ, 1 МБ, 2 МБ и неограниченный. По умолчанию установлено значение 1 МБ.  
  
 **Регистр для имен встроенных функций**  
 Указывает, используются ли в именах встроенных функций [!INCLUDE[tsql](../includes/tsql-md.md)], которые включены в список завершения, прописные буквы (например, DATEADD) или строчные буквы (например, dateadd). Выберите параметр, который в наибольшей степени согласуется с используемыми соглашениями по разработке кода [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок IntelliSense &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/troubleshooting-intellisense.md)  
  
  
