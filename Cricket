#include <stdio.h>
#include <string.h>


struct batsman {
    char name[25];
    int runs, balls, ones, twos, threes, fours, sixes;
    float str; 
} pl1[100];


struct bowler {
    char name[25];
    int runsgiven, wikettaken, over;
    float econmy; 
} pl2[100];

int main() {
    int plno, choice;
    int i, n, m;
    int total_runs = 0, total_wickets = 0, total_balls = 0;
    char search_name[25];

    printf("\n================== Cricket Score Sheet ==================\n");

   
    printf("\nEnter the number of batsmen: ");
    scanf("%d", &m);

    for (i = 0; i < m; i++) {
        printf("\nEnter the name of batsman %d: ", i + 1);
        scanf("%s", pl1[i].name);
        printf("Enter the number of ones scored by batsman %d: ", i + 1);
        scanf("%d", &pl1[i].ones);
        printf("Enter the number of twos scored by batsman %d: ", i + 1);
        scanf("%d", &pl1[i].twos);
        printf("Enter the number of threes scored by batsman %d: ", i + 1);
        scanf("%d", &pl1[i].threes);
        printf("Enter the number of fours hit by batsman %d: ", i + 1);
        scanf("%d", &pl1[i].fours);
        printf("Enter the number of sixes hit by batsman %d: ", i + 1);
        scanf("%d", &pl1[i].sixes);
        printf("Enter the number of balls faced by batsman %d: ", i + 1);
        scanf("%d", &pl1[i].balls);

      
        pl1[i].runs = (pl1[i].ones) + (2 * pl1[i].twos) + (3 * pl1[i].threes) + (4 * pl1[i].fours) + (6 * pl1[i].sixes);
        pl1[i].str = (pl1[i].balls > 0) ? (pl1[i].runs * 100.0f) / pl1[i].balls : 0.0f;

        
        total_runs += pl1[i].runs;
        total_balls += pl1[i].balls;
    }

    
    printf("\nEnter the number of bowlers: ");
    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        printf("\nEnter the name of bowler %d: ", i + 1);
        scanf("%s", pl2[i].name);
        printf("Enter the runs given by bowler %d: ", i + 1);
        scanf("%d", &pl2[i].runsgiven);
        printf("Enter the overs bowled by bowler %d: ", i + 1);
        scanf("%d", &pl2[i].over);
        printf("Enter the wickets taken by bowler %d: ", i + 1);
        scanf("%d", &pl2[i].wikettaken);

    
        total_wickets += pl2[i].wikettaken;
    }

    printf("\nThank you! All the information is recorded.\n");

   
    do {
        printf("\n================== Menu ==================\n");
        printf("1) Batsman Details by Number\n");
        printf("2) Bowler Details by Number\n");
        printf("3) Match Summary\n");
        printf("4) Highest Scorer\n");
        printf("5) Best Bowler\n");
        printf("6) Find Batsman by Name\n");
        printf("7) Find Bowler by Name\n");
        printf("8) Exit\n");
        printf("==========================================\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: // Batsman details by number
                printf("\nEnter the batsman number to see details (1-%d): ", m);
                scanf("%d", &plno);
                if (plno < 1 || plno > m) {
                    printf("Invalid batsman number!\n");
                    break;
                }
                plno--; // Adjust for zero-based indexing

                // Print batsman details
                printf("\n             Batsman Details\n");
                printf("==================================================================\n");
                printf("Batsman          Runs      Balls     Fours     Sixes      SR\n");
                printf("==================================================================\n");
                printf("%-15s %-10d %-10d %-10d %-10d %.2f\n\n",
                       pl1[plno].name,
                       pl1[plno].runs,
                       pl1[plno].balls,
                       pl1[plno].fours,
                       pl1[plno].sixes,
                       pl1[plno].str);
                break;

            case 2: 
                printf("\nEnter the bowler number to see details (1-%d): ", n);
                scanf("%d", &plno);
                if (plno < 1 || plno > n) {
                    printf("Invalid bowler number!\n");
                    break;
                }
                plno--; 

                
                pl2[plno].econmy = (pl2[plno].over > 0) ? (float)pl2[plno].runsgiven / pl2[plno].over : 0.0f;

                
                printf("\n             Bowler Details\n");
                printf("==================================================================\n");
                printf("Bowler           Runs Given   Overs     Wickets    Economy\n");
                printf("==================================================================\n");
                printf("%-15s %-12d %-10d %-10d %.2f\n\n",
                       pl2[plno].name,
                       pl2[plno].runsgiven,
                       pl2[plno].over,
                       pl2[plno].wikettaken,
                       pl2[plno].econmy);
                break;

            case 3: 
                printf("\n================== Match Summary ==================\n");
                printf("Total Runs Scored: %d\n", total_runs);
                printf("Total Wickets Taken: %d\n", total_wickets);
                printf("Total Balls Faced: %d\n", total_balls);
                printf("===================================================\n");
                break;

            case 4: { 
                int max_runs = 0, max_index = 0;
                for (i = 0; i < m; i++) {
                    if (pl1[i].runs > max_runs) {
                        max_runs = pl1[i].runs;
                        max_index = i;
                    }
                }
                printf("\nHighest Scorer: %s with %d runs.\n", pl1[max_index].name, max_runs);
                break;
            }

            case 5: { 
                int max_wickets = 0, max_index = 0;
                for (i = 0; i < n; i++) {
                    if (pl2[i].wikettaken > max_wickets) {
                        max_wickets = pl2[i].wikettaken;
                        max_index = i;
                    }
                }
                printf("\nBest Bowler: %s with %d wickets.\n", pl2[max_index].name, max_wickets);
                break;
            }

            case 6: 
                printf("\nEnter the batsman name to search: ");
                scanf("%s", search_name);
                for (i = 0; i < m; i++) {
                    if (strcmp(pl1[i].name, search_name) == 0) {
                        printf("\nBatsman Found: %s\n", pl1[i].name);
                        printf("Runs: %d, Balls: %d, Fours: %d, Sixes: %d, SR: %.2f\n",
                               pl1[i].runs, pl1[i].balls, pl1[i].fours, pl1[i].sixes, pl1[i].str);
                        break;
                    }
                }
                if (i == m)
                    printf("Batsman not found!\n");
                break;

            case 7: 
                printf("\nEnter the bowler name to search: ");
                scanf("%s", search_name);
                for (i = 0; i < n; i++) {
                    if (strcmp(pl2[i].name, search_name) == 0) {
                        printf("\nBowler Found: %s\n", pl2[i].name);
                        printf("Runs Given: %d, Overs: %d, Wickets: %d, Economy: %.2f\n",
                               pl2[i].runsgiven, pl2[i].over, pl2[i].wikettaken,
                               (pl2[i].over > 0) ? (float)pl2[i].runsgiven / pl2[i].over : 0.0f);
                        break;
                    }
                }
                if (i == n)
                    printf("Bowler not found!\n");
                break;

            case 8: 
                printf("Exiting program. Thank you!\n");
                break;

            default:
                printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 8);

    return 0;
}
