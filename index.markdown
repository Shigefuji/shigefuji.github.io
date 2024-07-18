---
layout: home
#layout: default
---
<!--
# プログラミング学習ブログへようこそ

## はじめに

このブログでは、プログラミングの基本から応用までを学んでいく過程を共有します。主に以下の内容について書いていきます。

- **プログラミング言語**: Python, C++ , C#
- **ツールと環境**: GitHub, VSCode, Docker,windows10,WOL2,RaspberryPi
- **プロジェクト**: 実際のプロジェクトを通じた学習

## 最新の投稿

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
-->

<!--

## こんな感じのサンプルコード

### C++での遺伝的アルゴリズムを使った「Hello, World!」 (ASCIIコードを使用しない)

```cpp
#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>
#include <algorithm>

const std::vector<int> TARGET = {8, 5, 12, 12, 15, 0, 23, 15, 18, 12, 4}; // "Hello, World!" -> {8, 5, 12, 12, 15, 0, 23, 15, 18, 12, 4}
const std::vector<int> CHARSET = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25}; // 'a' to 'z'
const int POPULATION_SIZE = 100;
const double MUTATION_RATE = 0.01;

struct Individual {
    std::vector<int> chromosome;
    int fitness;

    Individual() : chromosome(TARGET.size()), fitness(0) {}

    void calculate_fitness() {
        fitness = 0;
        for (size_t i = 0; i < TARGET.size(); ++i) {
            if (chromosome[i] == TARGET[i]) {
                fitness++;
            }
        }
    }
};

std::vector<int> random_chromosome() {
    std::vector<int> result;
    for (size_t i = 0; i < TARGET.size(); ++i) {
        result.push_back(CHARSET[rand() % CHARSET.size()]);
    }
    return result;
}

Individual crossover(const Individual &parent1, const Individual &parent2) {
    Individual child;
    for (size_t i = 0; i < TARGET.size(); ++i) {
        child.chromosome[i] = (rand() % 2) ? parent1.chromosome[i] : parent2.chromosome[i];
    }
    return child;
}

void mutate(Individual &individual) {
    for (size_t i = 0; i < TARGET.size(); ++i) {
        if (rand() / double(RAND_MAX) < MUTATION_RATE) {
            individual.chromosome[i] = CHARSET[rand() % CHARSET.size()];
        }
    }
}

void print_individual(const Individual &individual) {
    for (int gene : individual.chromosome) {
        if (gene == 0) {
            std::cout << " ";
        } else {
            std::cout << char(gene + 'a' - 1); // 'a' starts from 1
        }
    }
    std::cout << std::endl;
}

int main() {
    srand(time(0));

    std::vector<Individual> population(POPULATION_SIZE);
    for (auto &individual : population) {
        individual.chromosome = random_chromosome();
        individual.calculate_fitness();
    }

    int generation = 0;
    while (true) {
        std::sort(population.begin(), population.end(), [](const Individual &a, const Individual &b) {
            return a.fitness > b.fitness;
        });

        if (population[0].fitness == TARGET.size()) {
            break;
        }

        std::vector<Individual> new_population;
        for (int i = 0; i < POPULATION_SIZE; ++i) {
            Individual parent1 = population[rand() % (POPULATION_SIZE / 2)];
            Individual parent2 = population[rand() % (POPULATION_SIZE / 2)];
            Individual child = crossover(parent1, parent2);
            mutate(child);
            child.calculate_fitness();
            new_population.push_back(child);
        }

        population = new_population;
        generation++;

        std::cout << "Generation: " << generation << " | Best: ";
        print_individual(population[0]);
        std::cout << " | Fitness: " << population[0].fitness << std::endl;
    }

    std::cout << "Evolved to: ";
    print_individual(population[0]);
    std::cout << " in " << generation << " generations." << std::endl;

    return 0;
}
```



    Text can be **bold**, _italic_, or ~~strikethrough~~.
    [Link to another page](./another-page.html).
    There should be whitespace between paragraphs.
    There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.
    # Header 1
    This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.
    ## Header 2
    > This is a blockquote following a header.
    >
    > When something is important enough, you do it even if the odds are not in your favor.
    ### Header 3
    ```js
    // Javascript code with syntax highlighting.
    var fun = function lang(l) {
    dateformat.i18n = require('./lang/' + l)
        return true;
    }
    ```
    ```ruby
    # Ruby code with syntax highlighting
    GitHubPages::Dependencies.gems.each do |gem, version|
        s.add_dependency(gem, "= #{version}")
    end
    ```
    #### Header 4   
    *   This is an unordered list following a header.
    *   This is an unordered list following a header.
    *   This is an unordered list following a header.
    ##### Header 5
    1.  This is an ordered list following a header.
    2.  This is an ordered list following a header.
    3.  This is an ordered list following a header.
    ###### Header 6
    | head1        | head two          | three |
    |:-------------|:------------------|:------|
    | ok           | good swedish fish | nice  |
    | out of stock | good and plenty   | nice  |
    | ok           | good `oreos`      | hmm   |
    | ok           | good `zoute` drop | yumm  |
    ### There's a horizontal rule below this.
    * * *
    ### Here is an unordered list:
    *   Item foo
    *   Item bar
    *   Item baz
    *   Item zip
    ### And an ordered list:
    1.  Item one
    1.  Item two
    1.  Item three
    1.  Item four
    ### And a nested list:
    - level 1 item
        - level 2 item
        - level 2 item
            - level 3 item
            - level 3 item
    - level 1 item
        - level 2 item
        - level 2 item
        - level 2 item
    - level 1 item
        - level 2 item
        - level 2 item
    - level 1 item
    ### Small image
    ![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)
    ### Large image
    ![Branching](https://guides.github.com/activities/hello-world/branching.png)
    ### Definition lists can be used with HTML syntax.
    <dl>
    <dt>Name</dt>
    <dd>Godzilla</dd>
    <dt>Born</dt>
    <dd>1952</dd>
    <dt>Birthplace</dt>
    <dd>Japan</dd>
    <dt>Color</dt>
    <dd>Green</dd>
    </dl>
    ```
        Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
    ```
    <ul>
        {% for post in site.posts %}
            <li>
                <a href="{{ post.url }}">{{ post.title }}</a>
            </li>
        {% endfor %}
    </ul>


```
The final element.
```

--> 
