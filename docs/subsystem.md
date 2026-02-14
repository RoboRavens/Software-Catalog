You can get visual studio to generate a command by right clicking on a folder -> `Create a new class/command`. Choose `Subystem`, then type the name of the class. We suffix our Subsystem classes with "Subsystem".

Subsystems should 

```Java
public class ElevatorSubsystem extends SubsystemBase {
    // private instance variables should start with underscore
    private TalonFX _elevatorMotor = new TalonFX(RobotMap.ELEVATOR_MAIN_MOTOR_CAN_ID);
    private double _currentPosition = 0.0;

    public ElevatorSubsystem() {
        // runs once during robot initialization
        // used to initialize the subsystem
    }

    @Override
    public void periodic() {
        // the periodic method runs 50 times per second

        // reading motor position is expensive, so read it once per 20ms loop and save the reading locally.
        _currentPosition = _elevatorMotor.getPosition().getValueAsDouble();
    }

    // methods use camelCase (first letter of first word is lower case, next words start with upper case)
    public double getCurrentPosition() {
        return _currentPosition;
    }

    public double goToPosition(double position) {
        _elevatorMotor.setControl(new MotionMagicVoltage(this.targetPosition));
    }

    public void setPowerManually(double power) {
        _elevatorMotor.setControl(new DutyCycleOut(power).withEnableFOC(true));
    }
}
```