

```Java
public class Robot {
    // create one instance of the subsystem
    // can reference anywhere in the program using `Robot.ELEVATOR_SUBSYSTEM`
    public static final ElevatorSubsystem ELEVATOR_SUBSYSTEM = new ElevatorSubsystem();

    public Robot() {
        // initialize objects here
        ELEVATOR_SUBSYSTEM.setDefaultCommand(new ElevatorDefaultCommand());
    }

    @Override
    public void robotInit() {
        // initialize objects here, runs after Robot constructor
    }

    @Override
    public void robotPeriodic() {
        CommandScheduler.getInstance().run(); // this line must be here for Commands to execute
    }

    @Override
    public void disabledInit() {
        // runs once when entering disabled mode
        // similar methods exist for the other modes (autonomous/teleop/test)
    }

    @Override
    public void disabledPeriodic() {
        // runs 50 times per second when in disabled mode
        // similar methods exist for the other modes (autonomous/teleop/test)
    }

    @Override
    public void disabledExit() {
        // runs once when entering disabled mode
        // similar methods exist for the other modes (autonomous/teleop/test)
    }
}

```