	Задание: 
https://vk.com/doc135932718_464483873?hash=7745107b39692a71be&dl=55ad55a6199973583e

Скачиваем MatLab, на официальном сайте есть пробная версия для студенитов на 30 дней, только надо заполнить пару форм.

	Как настраивать фильтры: 
https://www.youtube.com/watch?v=utrb6DN-Pqc
	Как писать скрипт в MatLab:
https://www.youtube.com/channel/UCtuwVWw9H06uaTadcyO570A

	Презентации:
1. в общем про фильтры https://vk.com/doc322274866_459195487?hash=2efec4fdb91dc97346&dl=54ad218102da00e8cc
2. КИХ https://vk.com/doc322274866_459195488?hash=1cc9dd7f6f22ea047d&dl=cd35af91f33640f095
3. БИХ https://vk.com/doc322274866_459195489?hash=2c40336ffac4bb102d&dl=b96a7fe04704e6a3ff

Далее пример скрипта, сразу запускать(копировать в консоль) можно даже не пробовать так как нужно создать свои фильтры и вписать их вместо моего filBandpass1 (КИХ) и filLowpass (БИХ). И еще следует заменить мое уравнение sin(t) + cos(4*t) на свое.
vsize = 1024
le = 2*pi
step = le/(vsize-1)
t = 0:step:le
y = sin(t) + cos(4*t)
figure(1), plot(t, y), grid
Y = fft(y, vsize);
Pyy = Y.*conj(Y)/vsize;
f = 1000 * (0:(vsize/2-1))/vsize;
figure(3), plot(f, Pyy(1:(vsize/2))), grid
fY = filter(filBandpass1, Pyy(1:(vsize/2)))
figure(4), plot(f, fY), grid
fy = ifft(fY, vsize)
figure(5), plot(t, fy), grid

y = y + sin(450*t)
figure(8), plot(t, y), grid
fy = filter(filLowpass, y)
figure(9), plot(t, fy), grid


Далее из того что следует знать к моменту сдачи лабы:
1. Что такое КИХ и БИХ, как они работают, их уравнения, схемы?
2. Какой фильтр предполагает обратную связь и как он работает на первых итерациях, когда еще нет данных на его выходе?
3. Зачем нужны оконные преобразования?
4. Что это за такие НЧ, ВЧ, полосовые, режекторные фильтры?
5. Как получить полосовой и режекторный фильтр?
и т.д.
