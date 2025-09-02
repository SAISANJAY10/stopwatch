## AIM :

To create a simple Stopwatch Application using HTML, CSS, and JavaScript that can Start, Pause, and Reset time while displaying it in the format MM : SS : MS.

## PROCEDURE :

1 Create an HTML page with a display area and three buttons: Start, Pause, Reset.

2 Style the stopwatch using CSS to make it neat and centered.

3 Write JavaScript to:

   ~Start the timer using setInterval().

   ~Pause the timer using clearInterval().

   ~Reset the timer to 00 : 00 : 000.

4 Format the output to show minutes : seconds : milliseconds.

5 Run the program in a browser and test the buttons.

## PROGRAM :

~~~

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Stopwatch Application</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f4f4f9;
    }

    .stopwatch {
      text-align: center;
      background: #fff;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    }

    #display {
      font-size: 2.5rem;
      margin-bottom: 20px;
      font-weight: bold;
    }

    button {
      padding: 10px 20px;
      margin: 5px;
      font-size: 1rem;
      font-weight: bold;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.2s ease-in-out;
    }

    button:hover {
      transform: scale(1.05);
    }

    #start { background: #28a745; color: white; }
    #pause { background: #ffc107; color: white; }
    #reset { background: #dc3545; color: white; }
  </style>
</head>
<body>
  <div class="stopwatch">
    <div id="display">00 : 00 : 000</div>
    <button id="start">Start</button>
    <button id="pause">Pause</button>
    <button id="reset">Reset</button>
  </div>

  <script>
    let startTime, updatedTime, difference, tInterval;
    let running = false;

    const display = document.getElementById("display");
    const startBtn = document.getElementById("start");
    const pauseBtn = document.getElementById("pause");
    const resetBtn = document.getElementById("reset");

    function startTimer() {
      if (!running) {
        startTime = new Date().getTime() - (difference || 0);
        tInterval = setInterval(getShowTime, 10);
        running = true;
      }
    }

    function pauseTimer() {
      if (running) {
        clearInterval(tInterval);
        difference = new Date().getTime() - startTime;
        running = false;
      }
    }

    function resetTimer() {
      clearInterval(tInterval);
      running = false;
      difference = 0;
      display.innerHTML = "00 : 00 : 000";
    }

    function getShowTime() {
      updatedTime = new Date().getTime() - startTime;
      let minutes = Math.floor((updatedTime / (1000 * 60)) % 60);
      let seconds = Math.floor((updatedTime / 1000) % 60);
      let milliseconds = updatedTime % 1000;

      minutes = minutes < 10 ? "0" + minutes : minutes;
      seconds = seconds < 10 ? "0" + seconds : seconds;
      milliseconds = milliseconds < 100 ? 
                      (milliseconds < 10 ? "00" + milliseconds : "0" + milliseconds) : milliseconds;

      display.innerHTML = `${minutes} : ${seconds} : ${milliseconds}`;
    }

    startBtn.addEventListener("click", startTimer);
    pauseBtn.addEventListener("click", pauseTimer);
    resetBtn.addEventListener("click", resetTimer);
  </script>
</body>
</html>

~~~

## OUTPUT :

<img width="1919" height="1079" alt="Screenshot 2025-09-02 200552" src="https://github.com/user-attachments/assets/ad3a5809-be9f-40c5-9454-c56546320272" />

## RESULT :

A fully functional Stopwatch Application was successfully created.

The stopwatch can Start, Pause, and Reset.

The time is displayed dynamically in MM : SS : MS format.

The page does not refresh during operation.
