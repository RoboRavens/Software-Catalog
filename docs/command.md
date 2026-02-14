You can get visual studio to generate a command by right clicking on a folder -> `Create a new class/command`. Choose `Command`, then type the name of the class. We suffix our Command classes with "Command".

```Java
public class ElevatorGoToPositionCommand extends Command {
    private double _targetPosition;
    private double _lowerBound;
    private double _upperBound;

    public ElevatorGoToPositionCommand(double targetPosition) {
        // this let's the command scheduler know which subsystems this command uses
        // only one command can use a subsystem at a time
        addRequirements(Robot.ELEVATOR_SUBSYSTEM);

        // save target position and pre-calculate bounds
        _targetPosition = targetPosition;
        _lowerBound = targetPosition - buffer;
        _upperBound = targetPosition + buffer;
    }

    @Override
    public void initialize() {
        Robot.ELEVATOR_SUBSYSTEM.goToPosition(_targetPosition);
    }

    // Called every time the scheduler runs while the command is scheduled.
    @Override
    public void execute() {}

    // Called once the command ends or is interrupted.
    @Override
    public void end(boolean interrupted) {}

    // Returns true when the command should end.
    @Override
    public boolean isFinished() {
        var currentPosition = Robot.ELEVATOR_SUBSYSTEM.getCurrentPosition();
        if (currentPosition > _lowerBound && currentPosition < _upperBound) {
            // when the motor's position close enough to the target we end the command
            // returning true here ends the command
            return true;
        }

        return false;
    }
}
```