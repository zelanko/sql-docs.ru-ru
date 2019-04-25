---
title: Начало работы с SSMA для Sybase консоли (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 608457b1732d2c1cc188b4b419903d20faa642c8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62631961"
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Начало работы с SSMA для Sybase консоли (SybaseToSQL)
В этом разделе описывается процедура для запуска и начало работы с SSMA для Sybase консольное приложение. Здесь также перечислены правила используются в типичного окна выходных данных консоли SSMA.  
  
## <a name="launching-the-ssma-console"></a>Запуск консоли SSMA  
Следуйте инструкциям ниже, чтобы запустить приложение консоли SSMA:  
  
1.  Перейдите на начальном и затем выберите все программы.  
  
2.  Нажмите кнопку **SQL Server Migration Assistant для Sybase командной строки** ярлык.  
  
    Он отображает меню использования команд консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="using-the-ssma-console"></a>С помощью команд консоли SSMA  
После в системе Windows успешно запускается консоль, работать с ним можно использовать следующие действия:  
  
1.  Настройка команд консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе, см. в разделе [Создание файлов сценария &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
2.  [Создание файлов переменных значений &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [Выполнение команд консоли SSMA &#40;SybaseToSQL&#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) в соответствии с потребностями проекта. 
  
Дополнительные функции:  
  
1.  [Укажите пароль](managing-passwords-sybasetosql.md) и экспорта и импорта его на другие компьютеры окна.  
  
2.  [Создание отчетов](generating-reports-sybasetosql.md) для просмотра подробных xml вывод отчетов для оценки/преобразования и миграции данных. Можно также создавать отчеты подробные сведения об ошибке для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
При выполнении команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, и т.д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выходных данных принятое уникальный цвет. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; этому параметру в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
Цвет интерпретацию выходных данных консоли отображается в следующей таблице:  
  
|Color|Описание|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Отметка даты и времени, сообщение для пользователя|  
|Белый|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Строка для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
