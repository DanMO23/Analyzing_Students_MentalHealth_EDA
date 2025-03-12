# Analyzing Students' Mental Health

![Project Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![SQL](https://img.shields.io/badge/SQL-PostgreSQL-blue?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13.4-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=for-the-badge)

## Project Description

**Analyzing Students' Mental Health** is a project aimed at analyzing the mental health of international students at a Japanese university. The analysis is based on a survey conducted in 2018, which was published in 2019. The study found that international students are at a higher risk of mental health difficulties compared to the general population. Key factors such as social connectedness and acculturative stress were identified as predictors of depression.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Data Description](#data-description)
- [Analysis](#analysis)
- [Summary of the Results](#summary-of-the-results)
- [Conclusion](#conclusion)
- [Usage](#usage)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)
- [Author](#author)
- [License](#license)

## Prerequisites

Before starting, ensure you have the following tools installed on your machine:

- [Git](https://git-scm.com/)
- [PostgreSQL](https://www.postgresql.org/)

## Installation

Follow the steps below to set up the development environment:

1. **Clone the repository:**

   ```bash
   git clone https://github.com/DanMO23/Analyzing-Students-Mental-Health.git
   cd Analyzing-Students-Mental-Health
   ```

2. **Set up PostgreSQL database:**

   Create a PostgreSQL database and configure the connection settings in your environment.

3. **Load the data into the database:**

   Use the provided SQL scripts to load the data into your PostgreSQL database.

## Data Description

The dataset contains the following columns:

| Field Name      | Description                                      |
| --------------- | ------------------------------------------------ |
| `inter_dom`     | Types of students (international or domestic)    |
| `japanese_cate` | Japanese language proficiency                    |
| `english_cate`  | English language proficiency                     |
| `academic`      | Current academic level (undergraduate or graduate) |
| `age`           | Current age of student                           |
| `stay`          | Current length of stay in years                  |
| `todep`         | Total score of depression (PHQ-9 test)           |
| `tosc`          | Total score of social connectedness (SCS test)   |
| `toas`          | Total score of acculturative stress (ASISS test) |

## Analysis

The analysis explores the `students` data using PostgreSQL to determine if similar conclusions can be drawn for international students and to assess if the length of stay is a contributing factor.

### SQL Queries

1. **View All Data:**
    ```sql
    SELECT * 
    FROM students;
    ```

2. **Group by Length of Stay:**
    ```sql
    SELECT stay, COUNT(inter_dom) AS count_int, ROUND(AVG(todep), 2) AS average_phq, ROUND(AVG(tosc), 2) AS average_scs, ROUND(AVG(toas), 2) AS average_as
    FROM students
    WHERE inter_dom = 'Inter'
    GROUP BY stay
    ORDER BY stay DESC;
    ```

## Summary of the Results

The query groups international students by their length of stay and calculates the average scores for depression (PHQ-9), social connectedness (SCS), and acculturative stress (ASISS). Key insights include:

- **Length of Stay 10 Years**: Only 1 student with high depression (13.00) and acculturative stress (50.00) scores.
- **Length of Stay 8 Years**: Only 1 student with moderate depression (10.00) and high acculturative stress (65.00) scores.
- **Length of Stay 7 Years**: Only 1 student with low depression (4.00) and moderate acculturative stress (45.00) scores.
- **Length of Stay 6 Years**: 3 students with moderate depression (6.00) and acculturative stress (58.67) scores.
- **Length of Stay 5 Years**: Only 1 student with no depression (0.00) but very high acculturative stress (91.00) scores.
- **Length of Stay 4 Years**: 14 students with moderate depression (8.57) and very high acculturative stress (87.71) scores.
- **Length of Stay 3 Years**: 46 students with moderate depression (9.09) and high acculturative stress (78.00) scores.
- **Length of Stay 2 Years**: 39 students with moderate depression (8.28) and high acculturative stress (77.67) scores.
- **Length of Stay 1 Year**: 95 students with the lowest depression (7.48) and high acculturative stress (72.80) scores.

Overall, the results indicate that international students experience varying levels of depression and acculturative stress depending on their length of stay, with some students showing high levels of stress even after several years.

## Conclusion

This analysis highlights the mental health challenges faced by international students and underscores the importance of providing adequate support to help them cope with acculturative stress and maintain social connectedness.

## Usage

After completing the installation, you can run the SQL queries provided in the analysis section to explore the data and generate insights, or create your own queries to further analyze the dataset. If you have any questions or need assistance, feel free to open an issue.

## Technologies Used

- [PostgreSQL](https://www.postgresql.org/)

## Contributing

Contributions are welcome! Feel free to open issues and submit pull requests.

## Author

Developed by [DanMO23](https://github.com/DanMO23).

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
