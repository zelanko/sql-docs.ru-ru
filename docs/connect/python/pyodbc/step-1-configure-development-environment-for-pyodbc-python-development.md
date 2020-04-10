---
title: Шаг 1. Настройка среды разработки pyodbc в Python | Документация Майкрософт
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dd2063a527d782833f2abfcbd635de30aa27117
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926780"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Шаг 1. Настройка среды разработки для использования pyodbc в Python

## <a name="windows"></a>Windows  
Подключение к Базе данных SQL из Python с помощью pyodbc в ОС Windows.
  
1. **Скачивание установщика Python**.  
  Если на вашем компьютере не установлен язык Python, установите его. Перейдите на [страницу загрузки Python](https://www.python.org/downloads/windows/) и скачайте соответствующий установщик. Например, если вы используете 64-разрядный компьютер, скачайте установщик Python 2.7 или 3.7 (x64).  
  
2. **Установите Python**.  Завершив скачивание установщика, выполните следующие шаги. a. Дважды щелкните файл установщика, чтобы запустить его. b. Выберите язык и примите условия. c. Следуйте инструкциям на экране и дождитесь установки Python на компьютере. d. Чтобы убедиться, что Python установлен, перейдите в папку `C:\Python27` или `C:\Python37` и запустите `python -V` или `py -V` (для версии 3.x). 
      
3. [**Установка Microsoft ODBC Driver for SQL Server в Windows**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Запустите файл cmd.exe от имени администратора**.     

5. **Установите pyodbc с помощью диспетчера пакетов PIP для Python** (замените `C:\Python27\Scripts` путем к папке, где установлен Python).
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Подключение к базе данных SQL из Python с использованием pyodbc:
  
1. **Окно терминала**  

2. [**Установка Microsoft ODBC Driver for SQL Server в Linux**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Установка pyodbc**  
```  
> sudo -H pip install pyodbc
```
