---
title: Начало работы с SSMA для MySQL консоли (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 88cf4716ea02b8c5dbcbd73e9839c6bacfbed10b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075419"
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Начало работы с консолью SSMA для MySQL (MySQLToSQL)
В этом разделе описывается, как запустить и начало работы с MySQL консольного приложения. Также в списке, в данном документе, соглашения используются в типичного окна выходных данных консоли SSMA.  
  
## <a name="launching-ssma-console"></a>Запуск консоли SSMA  
Следуйте инструкциям ниже, чтобы запустить приложение консоли SSMA:  
  
1.  Перейдите к **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку **SQL Server Migration Assistant для командной строки MySQL** ярлык.  
  
    Он отображает меню использования команд консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После в системе Windows успешно запускается консоль, работать с ним можно использовать следующие действия:  
  
1.  Настройка команд консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе, см. в разделе [Создание файлов сценария &#40;MySQLToSQL&#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Создание файлов переменных значений &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Создание файлов подключения к серверу &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [Выполнение команд консоли SSMA &#40;MySQLToSQL&#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) в соответствии с потребностями проекта  
  
Дополнительные функции:  
  
1.  [Защита пароля](managing-passwords-mysqltosql.md) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Создание отчетов](generating-reports-mysqltosql.md) для просмотра подробных xml вывод отчетов для оценки /conversion и миграции данных. Подробные сведения об ошибке отчеты также могут формироваться для команд обновления и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
При выполнении команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, и т.д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выходных данных принятое уникальный цвет. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; этому параметру в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
Цвет Интерпретация выходных данных консоли в следующей таблице:  
  
|Color|Описание|  
|---------|---------------|  
|Красный|Неустранимая ошибка во время выполнения|  
|Серый|Отметка даты и времени, сообщение для пользователя|  
|Белый|Файл команд, тип сообщения|  
|Желтый|Предупреждение|  
|Зеленый|Строка для ввода данных пользователем|  
|Голубой|Начала, окончания и результат операции|  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для MySQL](installing-ssma-for-mysql-mysqltosql.md)  
  
