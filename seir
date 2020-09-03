%# SEIR-model--covid-19-in-peru
%This is a first attempt to see the behavior of covid 19 in peru using matlab. Be careful, this model is not 100% finished.
%primero correr esta primera parte en un archivo.m con el nombre ode_fun_simple
function dydt = ode_fun_simple(t, y,beta)

Death = 0.034;  % Death rate of COVID-19 (March, 2020)
Pre_infec = 5.2;
f = 1/Pre_infec;
Duration = 14;
r = 1/Duration;
S = y(1);
E= y(2);
I = y(3);

dS = -beta*I.*S;
dE = beta*I.*S -  f.*E;
dI = f*E - r*I;
dR = r*(1-Death)*I;
dD = (Death)*r*I;

dydt = [dS; dE; dI; dR; dD];
end
%%luego crear otro archivo .m con el nombre que usted desee y hacer correr el siguiente codigo
clear all; clc;

%% Parametros
Pre_infec = 5.2;
f = 1/Pre_infec;

Duration = 7;
r=1/Duration;

R_0 = 2.2; % Una sola persona infectada infectará a otras 2.2 personas en una población totalmente susceptible
N = 32.93e6; % poblacion del Peru
beta = R_0/(N*Duration);


%% Ecuaciones diferenciales
tspan = 0:1:365; % Observaremos lo que sucede durante el próximo año
y0 = [N-28, 0, 25, 3, 0]; % Recuento covid en peru

[t,y]=ode45(@(t,y) ode_fun_simple(t,y,beta), tspan, y0);

% ode45 es un solucionador de ecuaciones diferenciales numéricas integrado en MATLAB.

%% plot
plot(t,y,'LineWidth', 0.5, 'MarkerSize', 10)
legend('Susceptible','Expuestos','Infectados','Recuperados','Fallecidos', 'Location', 'Best')
xlabel('Días post 15 de marzo')
ylabel('Población')
title('SEIRQ en un año')
grid on;
grid minor;
set(gca, 'FontSize', 26)
%saveas(gcf, 'corona_simple1.png')


