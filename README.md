semaforo.ino

// ================= PINOS DE CONFIGURAÇÃO =================

// Pedestres – Via A
int verdepedestreA = 11;
int vermelhopedestreA = 12;

// Carros – Via A
int verdeA = 4;
int amareloA = 5;
int vermelhoA = 6;

// Pedestres – Via B
int verdepedestreB = 2;
int vermelhopedestreB = 3;

// Carros – Via B
int verdeB = 8;
int amareloB = 9;
int vermelhoB = 10;

// ================= FUNÇÃO FOR  =================

void piscarVermelhoPedestre(int led) {
  for (int i = 0; i < 5; i++) {
    digitalWrite(led, LOW);
    delay(500);
    digitalWrite(led, HIGH);
    delay(500);
  }
}

// ================= SETUP =================

void setup() {
  pinMode(verdepedestreA, OUTPUT);
  pinMode(vermelhopedestreA, OUTPUT);
  pinMode(verdeA, OUTPUT);
  pinMode(amareloA, OUTPUT);
  pinMode(vermelhoA, OUTPUT);

  pinMode(verdepedestreB, OUTPUT);
  pinMode(vermelhopedestreB, OUTPUT);
  pinMode(verdeB, OUTPUT);
  pinMode(amareloB, OUTPUT);
  pinMode(vermelhoB, OUTPUT);
}

// ================= LOOP =================

void loop() {

  // ===== ESTADO 1 =====
  // VIA A: CARROS VERDE | PEDESTRE A FECHADO
  // VIA B: CARROS VERMELHO | PEDESTRE B ABERTO

  // Via A
  digitalWrite(verdeA, HIGH);
  digitalWrite(amareloA, LOW);
  digitalWrite(vermelhoA, LOW);

  digitalWrite(verdepedestreA, LOW);
  digitalWrite(vermelhopedestreA, HIGH);

  // Via B
  digitalWrite(verdeB, LOW);
  digitalWrite(amareloB, LOW);
  digitalWrite(vermelhoB, HIGH);

  digitalWrite(verdepedestreB, HIGH);
  digitalWrite(vermelhopedestreB, LOW);

  delay(5000);

  // Aviso pedestre B
  digitalWrite(verdepedestreB, LOW);
  piscarVermelhoPedestre(vermelhopedestreB);
  digitalWrite(vermelhopedestreB, HIGH);

  // Amarelo Via A
  digitalWrite(verdeA, LOW);
  digitalWrite(amareloA, HIGH);
  delay(2500);

  digitalWrite(amareloA, LOW);
  digitalWrite(vermelhoA, HIGH);

  // ===== ESTADO 2 =====
  // VIA B: CARROS VERDE | PEDESTRE B FECHADO
  // VIA A: CARROS VERMELHO | PEDESTRE A ABERTO

  // Via A
  digitalWrite(verdeA, LOW);
  digitalWrite(amareloA, LOW);
  digitalWrite(vermelhoA, HIGH);

  digitalWrite(verdepedestreA, HIGH);
  digitalWrite(vermelhopedestreA, LOW);

  // Via B
  digitalWrite(verdeB, HIGH);
  digitalWrite(amareloB, LOW);
  digitalWrite(vermelhoB, LOW);

  digitalWrite(verdepedestreB, LOW);
  digitalWrite(vermelhopedestreB, HIGH);

  delay(5000);

  // Aviso pedestre A
  digitalWrite(verdepedestreA, LOW);
  piscarVermelhoPedestre(vermelhopedestreA);
  digitalWrite(vermelhopedestreA, HIGH);

  // Amarelo Via B
  digitalWrite(verdeB, LOW);
  digitalWrite(amareloB, HIGH);
  delay(2500);

  digitalWrite(amareloB, LOW);
  digitalWrite(vermelhoB, HIGH);
}
