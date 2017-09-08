---
title: "Начало работы с SSMA для Sybase консоли (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 239b7a8f4dbc3069e67d680b319bf426a0f917e6
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-sybase-console-sybasetosql"></a>Начало работы с SSMA для Sybase консоли (SybaseToSQL)
В этом разделе описывается, как запустить и приступить к работе с Sybase консольного приложения. Также перечислены в настоящем документе, соглашения используются в типичного окна вывода консоли SSMA.  
  
## <a name="launching-ssma-console"></a>При запуске консоли SSMA  
Чтобы запустить консольное приложение SSMA используйте следующие действия:  
  
1.  Перейдите на начальном экране и выберите все программы.  
  
2.  Нажмите кнопку **SQL Server Migration Assistant для Sybase командной строки** ярлык.  
  
    Отображает меню использования консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После консоль успешно запускается в среде Windows, можно выполнить следующие действия для работы с ней:  
  
1.  Настройка консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40; SybaseToSQL &#41; ](../../ssma/sybase/creating-script-files-sybasetosql.md) .  
  
2.  [Создание файлов значение переменной &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Создание файлов подключения сервера &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [Выполнение консоли SSMA &#40; SybaseToSQL &#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) зависимости от потребностей проекта  
  
Дополнительные функции:  
  
1.  [Укажите пароль](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Составление отчетов](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e) для просмотра xml подробный вывод отчетов для оценки миграции /conversion и данных. Подробные сведения об ошибке отчеты также можно создать для команд обновить и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, т. д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выводе обозначается уникальным цветом. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли Ssma_sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "вывод консоли Ssma_sybase")  
  
Интерпретация цветовой выходные данные в консоли в следующей таблице:  
  
|Color|Description|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Метка даты и времени, сообщение для пользователя|  
|White|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Запрос для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
  

