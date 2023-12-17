//create Model class

class Model {
    private int rows;
    private int cols;
    private int[][] currentGeneration;
    private int[][] nextGeneration;

    public Model(int rows, int cols) {
        this.rows = rows;
        this.cols = cols;
        this.currentGeneration = new int[rows][cols];
        this.nextGeneration = new int[rows][cols];
        initializeGlider();
    }

    public int getRows() {
        return rows;
    }

    public int getCols() {
        return cols;
    }

    public int[][] getCurrentGeneration() {
        return currentGeneration;
    }

    public void initializeGlider() {
        currentGeneration[0][1] = 1;
        currentGeneration[1][2] = 1;
        currentGeneration[2][0] = 1;
        currentGeneration[2][1] = 1;
        currentGeneration[2][2] = 1;
    }

    public void updateNextGeneration() {
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                int liveNeighbors = countLiveNeighbors(i, j);
                if (currentGeneration[i][j] == 1) {
                    nextGeneration[i][j] = (liveNeighbors == 2 || liveNeighbors == 3) ? 1 : 0;
                } else {
                    nextGeneration[i][j] = (liveNeighbors == 3) ? 1 : 0;
                }
            }
        }
    }

    private int countLiveNeighbors(int row, int col) {
        int count = 0;
        for (int i = -1; i <= 1; i++) {
            for (int j = -1; j <= 1; j++) {
                int neighborRow = (row + i + rows) % rows;
                int neighborCol = (col + j + cols) % cols;
                count += currentGeneration[neighborRow][neighborCol];
            }
        }
        count -= currentGeneration[row][col];
        return count;
    }

    public void updateCurrentGeneration() {
        int[][] temp = currentGeneration;
        currentGeneration = nextGeneration;
        nextGeneration = temp;
    }
}
