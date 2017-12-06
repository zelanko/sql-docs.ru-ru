---
title: "Начало работы с SSMA для MySQL консоли (MySQLToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
caps.latest.revision: "23"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab719f68ed7fb2718052c5ba4816dd7be963b494
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Начало работы с SSMA для MySQL консоли (MySQLToSQL)
В этом разделе описывается, как запустить и приступить к работе с MySQL консольного приложения. Также перечислены в настоящем документе, соглашения используются в типичного окна вывода консоли SSMA.  
  
## <a name="launching-ssma-console"></a>При запуске консоли SSMA  
Чтобы запустить консольное приложение SSMA используйте следующие действия:  
  
1.  Последовательно выберите пункты **запустить** и пункты **все программы**.  
  
2.  Нажмите кнопку **SQL Server Migration Assistant для MySQL командной строки** ярлык.  
  
    Отображает меню использования консоли SSMA и `(/? Help)`, чтобы помочь вам приступить к работе с консольного приложения.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Процедура использования консоли SSMA  
После консоль успешно запускается в среде Windows, можно выполнить следующие действия для работы с ней:  
  
1.  Настройка консоли SSMA через файлы скриптов. Дополнительные сведения об этом разделе см. в разделе [Создание файлов скриптов &#40; MySQLToSQL &#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Создание файлов значение переменной &#40; MySQLToSQL &#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Создание файлов подключения сервера &#40; MySQLToSQL &#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [Выполнение консоли SSMA &#40; MySQLToSQL &#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) зависимости от потребностей проекта  
  
Дополнительные функции:  
  
1.  [Защита паролем](http://msdn.microsoft.com/en-us/4ffbc587-ea3f-49ad-bc42-a654f672325e) и экспортировать и импортировать его на других компьютерах окна  
  
2.  [Составление отчетов](http://msdn.microsoft.com/en-us/1c0202e8-546d-4cb3-a37f-1d2e35d53839) для просмотра xml подробный вывод отчетов для оценки миграции /conversion и данных. Подробные сведения об ошибке отчеты также можно создать для команд обновить и синхронизации.  
  
## <a name="ssma-console-output-conventions"></a>Соглашения о выходных данных консоли SSMA  
После выполнения команды сценария SSMA и параметры, консольная программа отображает результаты и сообщения (сведения, ошибка, т. д.) для пользователя на консоли или при необходимости перенаправляет выходные данные в XML-файл. Каждый тип сообщения в выводе обозначается уникальным цветом. Например текстовое сообщение в белый цвет обозначает команд файла скрипта; в зеленый цвет представляет запрос для ввода данных пользователем и т. д.  
  
![Вывод консоли Ssma_mysql](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "вывод консоли Ssma_mysql")  
  
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
[Установка SSMA для MySQL](http://msdn.microsoft.com/en-us/e89b45bd-59c1-4d23-8bd7-3dafc1947448)  
  
