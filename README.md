# LedMultiplexing Arduino Code
int LEDR[] = {6, 7, 8}; // anod
int LEDC[] = {A3, A4, A5}; // catod
int n =3;

void setup()
{
  Serial.begin(9600);
  for (int i = 0; i < n; i++)
  {
    pinMode(LEDR[i], OUTPUT);
    digitalWrite(LEDR[i], LOW);
    pinMode(LEDC[i], OUTPUT);
    digitalWrite(LEDC[i], HIGH);
  }
}
void led(int istart, int jstart)
{
  digitalWrite(LEDR[istart], HIGH);
  digitalWrite(LEDC[jstart], LOW);
  delay(1000);
  digitalWrite(LEDC[jstart], HIGH);
  digitalWrite(LEDR[istart], LOW);

}

void loop()
{
  int randi = random(0, 3);
  int randj = random(0, 3);
  Serial.print(randi);
  Serial.print(" ");
  Serial.println(randj);
  led(randi, randj);
}
