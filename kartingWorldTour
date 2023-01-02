#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define NUM_KARTS 5
#define NUM_LAPS 5

struct Kart {
  int position;
  char name[32];
  int laps_completed;
  double lap_times[NUM_LAPS];
  double total_time;
};

void init_karts(struct Kart* karts) {
  for (int i = 0; i < NUM_KARTS; i++) {
    sprintf(karts[i].name, "Kart %d", i + 1);
    karts[i].laps_completed = 0;
    karts[i].total_time = 0.0;
  }
}

void simulate_lap(struct Kart* karts) {
  for (int i = 0; i < NUM_KARTS; i++) {
    double lap_time = (double)rand() / RAND_MAX * 20.0 + 10.0;
    karts[i].lap_times[karts[i].laps_completed] = lap_time;
    karts[i].total_time += lap_time;
    karts[i].laps_completed++;
  }
}

void sort_karts(struct Kart* karts) {
  for (int i = 0; i < NUM_KARTS; i++) {
    for (int j = i + 1; j < NUM_KARTS; j++) {
      if (karts[i].total_time > karts[j].total_time) {
        struct Kart temp = karts[i];
        karts[i] = karts[j];
        karts[j] = temp;
      }
    }
  }
}

int main() {
  srand(time(NULL));

  struct Kart karts[NUM_KARTS];
  init_karts(karts);

  for (int i = 0; i < NUM_LAPS; i++) {
    simulate_lap(karts);
    sort_karts(karts);
    for (int j = 0; j < NUM_KARTS; j++) {
      printf("%s: %d laps, %.2lf seconds\n", karts[j].name, karts[j].laps_completed, karts[j].total_time);
    }
    printf("\n");
  }

  return 0;
}
