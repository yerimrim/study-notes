<aside>
💡

### Designing for Performance

- **Microprocessor speed**
    - Pipelining
        
        : 프로세서가 데이터 또는 명령어를 여러 단계로 나누어 동시에 처리 → 처리 속도 UP
        
        enables a processor to work simultaneously on multiple instructions by performing a different phase for each of the multiple instructions at the same time.
        
    - Branch prediction
        
        : 프로세서가 메모리에서 가져온 명령어를 분석해 어떤 명령어 그룹이 다음에 처리될지 예측하여 실행 준비.
        
    - Superscalar execution
        
        : 한 프로세서 클록 사이클당 여러 개의 명령어를 동시에 실행.
        
    - Data flow analysis
        
        : 프로세서가 명령어 간 데이터 의존성을 분석해 최적의 명령어 실행 순서를 만듦.
        
    - Speculative execution
        
        : 프로그램에서 실제로 필요한 명령어가 실행되기 전에 일부 명령어를 미리 실행하고 결과를 임시로 저장.
        

- **Performance balance**
    - Must adjust the ‘Organization’ and ‘Architecture’

- **Improvements in Chip Organization and Architecture**
    - Shrinking logic gate size (⇒ 작은 크기의 logic gate가 하나의 칩에 더 많이 배치됨)
        
        ⇒ The number of gates, density of the chips will be increased.
        
        ⇒ Clock rate will be increased ⇒ 성능 up, 전력 소비 up, 열 발산 up
        
        ⇒ Propagation time for signals will be decreased.
        
    - Increase the size and speed of Caches
        
        ⇒ Dedicates processor chip
        
        ⇒ Cache access times will be decreased significantly.
        
    - Parallelism (Parallel arrangement)
        
        ⇒ The speed of instruction execution will be increased.
        
</aside>

<aside>
💡

### Multicore & MIC (Many Integrated Core)

- Multicore

: The use of multiple processors on the same chip.

- MIC (Many Integrated Core)

: The use of many (more than two) processors on the same chip.

**Strategy**: use general purpose processors (simpler processors) on a sigle chip.

**Result**: Multicore & MIC increases performance without increasing clock rate.

</aside>

<aside>
💡

### GPGPU (General Purpose Graphic Processing Unit)

: Core designed to perfrom parallel operations on graphics data.

</aside>

<aside>
💡

### Amdahl’s Law

: Deals with the potential speedup of a program using mutiple-processors compared to a single-processor.

⇒ 컴퓨터 시스템의 일부를 개선할 때, 전체적으로 얼마만큼의 최대 성능 향상이 있는지 계산하는 데 사용됨.

</aside>

<aside>
💡

### Little’s Law

Represents the relationship between inventory, output rate, and flow time in a steady state.

𝑳 = 𝝀 × 𝑾

𝑳 : the average number of items in the system (사용자 수)

𝝀 : the arrival rate of items (시스템 처리량)

𝑾 : the average time an item spends in the system. (응답시간)

* 𝝀 (시스템 처리량) is proportional to 𝑳 (사용자 수), inversely proportional to 𝑾 (응답시간)

</aside>

<aside>
💡

### Basic measures of computer performance

- Clock rate (clock speed): the rate of pulses.
- Clock cycle: one pulse of the clock.
- Cycle time: the time between pulses.

* A straight comparison of clock speeds  doesn’t tell the whole story about performance.

</aside>

<aside>
💡

### Calculating the mean

- Arithmetic mean (산술평균)
    - 데이터가 고르게 분포되어 있을 때, 대표값을 잘 나타냄
    - 이상치(특히 큰 값)가 있을 때 값이 왜곡될 수 있음.
- Geometric mean (기하평균)
    - **극단값의 영향**을 덜 받음
    - **음수 값**이나 **0**이 포함될 경우 기하평균은 정의되지 않음.
    - 값이 **비율**이나 **변동률**일 때 유용
- Harmonic mean (조화평균)
    - **작은 값**이 있는 데이터에 민감
    - **비율**이나 **속도** 같은 값을 비교할 때 유용
</aside>

<aside>
💡

### Benchmark

- : A program written in a high-level language.
    
    ⇒ So, Benchmark can be used on any different machines.
    

- **SPEC Benchmarks**
    - SPEC CPU2017 is the best known benchmark suite of SPEC.
    - Appropriate to measure applications’ performance.
- **Terms used in SPEC Documentation**
    - System under test
        
        : A system to be evaluated.
        
    - Reference machine
        
        : A system used to establish a baseline perfomance for all benchmarks.
        
    - Base metric
        
        : A measurement used as a reference point for evaluating the performance.
        
    - Peak metric
        
        : A measurement that indicates the maximum performance, capability, or output of a system.
        
    - Speed metric
        
        : A measurement of time it takes to execute a compiled benchmark.
        
    - Rate metric
        
        : A measurement of how many tasks a computer can accomplish in a certain amount of time.
        
</aside>
