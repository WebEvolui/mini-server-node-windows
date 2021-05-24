# Mini Server Node Windows
Rodar script node no windows de forma automática (mesmo desligando e ligando máquina o processo volta a rodar)

## Requisitos
- Windows 
- Node instalado e configurado

## Projeto
O seu projeto já deve ficar rodando constantimente
Se não for o caso ainda, use um pacote como o [Cron](https://www.npmjs.com/package/cron)

> Ex:
```
var { buscaNovidades } = require("./index");
var CronJob = require('cron').CronJob;


var job = new CronJob('0 */10 * * * *', function () {
    buscaNovidades();
}, null, true, 'America/Sao_Paulo');
job.start();
```

## Projeto já configurado, vamos instalar alguns pacotes
> Instale como *administrador* no **CMD ou Terminal Windows** o [PM2](https://pm2.keymetrics.io/docs/usage/quick-start/)
> 
> Até aqui teremos um gerenciador de processos instalado
```
$ npm install pm2@latest -g
# or
$ yarn global add pm2
```

### Inicie o seu App
```
pm2 start app.js
```

> Instale como *administrador* no **CMD ou Terminal Windows**
> 
> Instalando um pacote que vai iniciar o PM2 sempre que o seu PC ligar: [pm2-windows-startup](https://github.com/marklagendijk/node-pm2-windows-startup) *meio abandonado* 
> 
> PM2 recomenda [pm2-installer](https://github.com/jessety/pm2-installer), para servidor (windows) parece que é o caminho, para win10 comum funciona o anterior tranquilo!
```
npm install pm2-windows-startup -g
pm2-startup install

pm2 save   
# O "save" salva o que você iniciou anteriormente, e quando o PM2 iniciar novamente ele vai iniciar tudo o que tinha antes
```

### Pronto tudo configurado
Pode deixar o script rodando, desligar e ligar o windows que ele vai continuar rodando

## Aplicações
As vezes vocês tem um script simples que gostaria que ficasse rodando, mas *não quer colocar na Web* ou *ele demanda muitos recursos* de um servidor e ficaria elevado o custo! 
