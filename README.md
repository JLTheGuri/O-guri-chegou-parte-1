# Bem vindos ao meu perfil

Meu nome é josé LUcas conhecido como *O Guri*
.Estou estudando na alura
.estou me desenvolvendo na linguagem javascript
.ultilizo essse espaço para organização dos projetos e estudos desenvolvidos.

### Entre em contato comigo
00001122484483sp@al.educacao.sp.gov.br
![](https://media.tenor.com/syqk8AK7JAsAAAAM/muito-feliz-palmeiras.gif)

projetinho abaixo p5.sj
Ping pong dos guri:

//variáveis da bolinha gurizinha
let xBolinha = 100;
let yBolinha = 200;
let diametro = 22;
let raio = diametro / 2;

//velocidade da bolinha gurizista
let velocidadeXBolinha = 6;
let velocidadeYBolinha = 6;

//variáveis da raquete guriazinha
let xRaquete = 5;
let yRaquete = 150;
let raqueteComprimento = 10;
let raqueteAltura = 90;

//variáveis do oponente guri
let xRaqueteOponente = 585;
let yRaqueteOponente = 150;
let velocidadeYOponente;

let colidiu = false;

//placar do jogo de guri
let meusPontos = 0;
let pontosDoOponente = 0;

//audio do jogo
let ponto;
let trilha;


function setup() {
  createCanvas(600, 400);
}

function draw() {
  background(0);
  mostraBolinha();
  movimentaBolinha();
  verificaColisaoBorda();
  mostraRaquete(xRaquete, yRaquete);
  mostraRaquete(xRaqueteOponente, yRaqueteOponente);
  movimentaMinhaRaquete();
  // verificaColisaoRaquete();
  verificaColisaoRaquete(xRaquete, yRaquete);
  verificaColisaoRaquete(xRaqueteOponente, yRaqueteOponente);
  movimentaRaqueteOponente();
  incluiPlacar()
  {textSize(23);
   textAlign(CENTER);
  }
  
  marcaPonto();
}

function mostraBolinha() {
  circle(xBolinha, yBolinha, diametro);
}

function movimentaBolinha() {
  xBolinha += velocidadeXBolinha;
  yBolinha += velocidadeYBolinha;
}

function verificaColisaoBorda() {
  if (xBolinha + raio > width || xBolinha - raio < 0) {
    velocidadeXBolinha *= -1;
  }
  if (yBolinha + raio > height || yBolinha - raio < 0) {
    velocidadeYBolinha *= -1;
  }
}

function mostraRaquete(x,y) {
  rect(x, y, raqueteComprimento, raqueteAltura);
}

function movimentaMinhaRaquete() {
  if(keyIsDown(UP_ARROW)) {
    yRaquete -= 10;
  }
  if(keyIsDown(DOWN_ARROW)) {
    yRaquete += 10;
  }
}

function verificaColisaoRaquete() {
  if (xBolinha - raio < xRaquete + raqueteComprimento && yBolinha - raio < yRaquete + raqueteAltura && yBolinha + raio > yRaquete) {
    velocidadeXBolinha *= -1;
  }
}

function verificaColisaoRaquete(x,y) {
  colidiu = collideRectCircle(x, y, raqueteComprimento, raqueteAltura, xBolinha, yBolinha, raio);
  if(colidiu) {
    velocidadeXBolinha *= -1;
  }
}

function movimentaRaqueteOponente() {
  velocidadeYOponente = yBolinha - yRaqueteOponente - raqueteComprimento / 2 - 30;
  yRaqueteOponente += velocidadeYOponente;
}

function incluiPlacar() {
  fill(255);
  text(meusPontos, 150,26);
  text(pontosDoOponente, 450,26);
}

function marcaPonto() {
  if (xBolinha > 590) {
    meusPontos += 1;
  }
  if (xBolinha < 10) {
    pontosDoOponente += 1;
  }
}


function bolinhaNaoFicaPresa(){
    if (XBolinha - raio < 0){
    XBolinha = 23
    }
}
